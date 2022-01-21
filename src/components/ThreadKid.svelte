<script lang="ts">
    import { Link } from "svelte-routing";

    export let kid;
</script>

<div class="hightlight">
    <Link to="/user/{kid['by']}">{kid['by']}</Link>
    {#if kid.hasOwnProperty("dead")}
        <p>DELETED</p>
    {:else}
        <p class="comment">{@html kid['text']}</p>
    {/if}
</div>