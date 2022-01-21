<script lang="ts">
    export let kid;
</script>

<div class="hightlight">
    <h3>{kid['by']}</h3>
    {#if kid.hasOwnProperty("dead")}
        <p>DELETED</p>
    {:else}
        <p class="comment">{@html kid['text']}</p>
    {/if}
</div>