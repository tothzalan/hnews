<script lang="ts">
    export let item;
</script>

<div>
    <h2>{item['title']}</h2>
    <p>By:  {item['by']}</p>
    <p>Replies: {item['descendants']}</p>
    <a href={item['url']}>Open Link</a>
</div>