<script lang="ts">
    import { Link } from "svelte-routing";

    export let userData: JSON;

    let accountCreated: Date = new Date(userData['created'] * 1000);
    let date: string = `${accountCreated.getUTCFullYear()}/${accountCreated.getUTCMonth()}/${accountCreated.getUTCDay()}`
</script>

<h2>{userData['id']}</h2>
<p>Karma: {userData['karma']}</p>
<p>Created: {date}</p>
{#if userData.hasOwnProperty("about")}
    <p>{@html userData['about']}</p>
{/if}
<Link to="/">Go back</Link>