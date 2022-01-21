<script lang="ts">
    import { Link } from "svelte-routing";

    export let item;
</script>

<div>
    <h2>{item['title']}</h2>
    <Link to="/user/{item['by']}">- {item['by']}</Link>
    <p>Replies: {item['descendants']}</p>
    <a href={item['url']}>Open Link</a>
</div>