<script lang="ts">
    import { Link } from "svelte-routing";

    export let item: JSON;
    export let index: number;
</script>

<div class="hightlight">
    <h2><a href={item['url']}>{index+1}. {item['title']}</a></h2>
    <Link to="/user/{item['by']}">By: {item['by']}</Link>
    <p>Replies: {item['descendants']}</p>
    <Link to="/thread/{item['id']}">Open Thread</Link>
</div>