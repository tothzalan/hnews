<script lang="ts">
	import { Router, Link, Route } from "svelte-routing";
	import Home from "./routes/Home.svelte";
	import Thread from "./routes/Thread.svelte";
	import User from "./routes/User.svelte";

	export let url: string = "";
</script>

<svelte:head>
	<title>HNews</title>
</svelte:head>

<Router {url}>
	<nav class="navBar">
		<Link to="/">Home</Link>
		<Link to="/user">User</Link>
	</nav>
	<main>
		<Route path="thread/:id" let:params><Thread id={+params.id}></Thread></Route>
		<Route path="user"><User></User></Route>
		<Route path="user/:username" let:params><User username={params.username}></User></Route>
		<Route path="/"><Home /></Route>
	</main>
</Router>