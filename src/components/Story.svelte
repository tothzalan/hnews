<script lang="ts">
    import { Link } from "svelte-routing";

    export let item: JSON;
    export let index: number;
</script>

<div class="hightlight">
    <h2>{index+1}. {item['title']} - {item['by']}</h2>
    <p>Replies: {item['descendants']}</p>
    <a href={item['url']}>Open Link</a>
    <br/>
    <Link to="/thread/{item['id']}">Open Thread</Link>
</div>