<script lang="ts">
    import { onMount } from "svelte";
    import Story from "../components/Story.svelte";

    let results: Array<JSON>;

    /*
        https://github.com/HackerNews/API
    */
    onMount(async () => {
        const resTopFH: any = await fetch("https://hacker-news.firebaseio.com/v0/topstories.json");
        let topStories: Array<number> = await resTopFH.json();

        results = await Promise.all(topStories.slice(0, 15).map(async (nthItem): Promise<JSON> => {
            return await getItem(nthItem);
        }));
    });

    async function getItem(nthItem: number): Promise<JSON> {
        const res: any = await fetch(`https://hacker-news.firebaseio.com/v0/item/${nthItem}.json`);
        return await res.json();
    }

</script>

<h1>HNews</h1>
<div class="container">
    {#if results}
        {#each results as item, index}
                <Story index={+index} item={item}></Story>
        {/each}
    {:else}
        <h2>Loading...</h2>
    {/if}
</div>
