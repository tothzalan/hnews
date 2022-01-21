<script lang="ts">
    import { onMount } from "svelte";
    import User from "../components/User.svelte";

    export let username: string;

    let userData: JSON;

    onMount(async () => {
        const resGetUser: any = await fetch(`https://hacker-news.firebaseio.com/v0/user/${username}.json`);
        userData = await resGetUser.json();
    });

</script>

<div class="container">
    {#if userData}
        <User userData={userData} />
    {:else}
        <p>Loading ...</p>
    {/if}
</div>