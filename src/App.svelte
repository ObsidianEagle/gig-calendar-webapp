<script>
	import { onMount } from 'svelte';
	import ListItem from './ListItem.svelte';

	export let gigs = [];

	onMount(() => {
		fetch('https://gig-calendar-node-api.herokuapp.com/')
			.then((res) => res.json())
			.then((data) => {
				gigs = data.values.slice(1);
			});
	})
</script>

<main>
	<h1>Upcoming Gigs</h1>
	<hr />
	{#each gigs as gig (gig)}
		<ListItem artist={gig[0]} venue={gig[1]} date={gig[2]} supports={gig[4]} />
		<hr />
	{/each}
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
		color: #ddd;
		background-color: #1A1A1A;
	}

	h1 {
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
