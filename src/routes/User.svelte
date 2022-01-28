<script lang="ts">
    import { onMount } from "svelte";
    import User from "../components/User.svelte";

    export let username: string;
    let usernameInput: string;

    let userData: JSON;

    onMount(async () => {
        if(username) {
            await getUserData(username);
        }
    });

    async function getUserData(name: string) {
        const resGetUser: any = await fetch(`https://hacker-news.firebaseio.com/v0/user/${name}.json`);
        userData = await resGetUser.json();
    }

    async function inputKeyUp(e: KeyboardEvent) {
        if(e.keyCode == 13)
            await getUserData(usernameInput);    
    }

</script>


<div class="container">
    {#if !username}
        <input bind:value={usernameInput} on:keyup={inputKeyUp}>
        <button on:click|preventDefault={()=> { getUserData(usernameInput)}}>Get user</button>
    {/if}
    {#if userData}
        <User userData={userData} />
    {/if}
</div>