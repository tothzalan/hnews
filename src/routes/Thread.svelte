<script lang="ts">
    import { onMount } from "svelte";
import App from "../App.svelte";
    import ThreadItem from "../components/ThreadItem.svelte";
    import ThreadKid from "../components/ThreadKid.svelte";
import Home from "./Home.svelte";

    export let id: number;

    let item: JSON;
    let kids: Array<JSON>;

    onMount(async () => {
        const resGetItem: any = await fetch(`https://hacker-news.firebaseio.com/v0/item/${id}.json`);
        item = await resGetItem.json();

        kids = await Promise.all(item['kids'].map(async (kid): Promise<JSON> => {
            return await getItem(kid);
        }));
    });

    async function getItem(kid: number): Promise<JSON> {
        const res: any = await fetch(`https://hacker-news.firebaseio.com/v0/item/${kid}.json`);
        return await res.json();
    }
</script>


<div class="container">
    {#if item}
        <ThreadItem item={item} />
    {/if}
    {#if kids}
        {#each kids as kid}
            <ThreadKid kid={kid} />
        {/each}
    {:else}
        <h2>Loading comments...</h2>
    {/if}
</div>