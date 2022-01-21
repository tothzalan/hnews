<script lang="ts">
	import { Router, Link, Route } from "svelte-routing";
	import Home from "./routes/Home.svelte";
	import Thread from "./routes/Thread.svelte";

	export let url: string = "";
</script>

<svelte:head>
	<title>HNews</title>
</svelte:head>

<Router {url}>
	<nav class="navBar">
		<Link to="/">Home</Link>
	</nav>
	<main>
		<Route path="thread/:id" let:params><Thread id={+params.id}></Thread></Route>
		<Route path="about"><p>About</p></Route>
		<Route path="/"><Home /></Route>
	</main>
</Router>