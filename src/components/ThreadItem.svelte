<script lang="ts">
    import { Link } from "svelte-routing";

    export let item;

    let timeCreated: Date = new Date(item['time'] * 1000);
    let date: string = `${timeCreated.getUTCFullYear()}/${timeCreated.getUTCMonth()}/${timeCreated.getUTCDay()}`
</script>

<div>

    <h2>{item['title']}</h2>
    <Link to="/user/{item['by']}">- {item['by']}</Link>
    <p>Replies: {item['descendants']}</p>
    <p>{date}</p>
    <a href={item['url']}>Open Link</a>
</div>