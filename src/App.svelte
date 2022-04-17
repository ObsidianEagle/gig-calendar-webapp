<script>
	import { onMount } from 'svelte';
	import ExternalLink from './ExternalLink.svelte';
	import ListItem from './ListItem.svelte';
	import LoadingSpinner from './LoadingSpinner.svelte';

	let gigs = [];
	let loading = true;
	let errorOccured = false;

	onMount(() => {
		fetch('https://gig-calendar-node-api.herokuapp.com/')
			.then((res) => res.json())
			.then((data) => {
				gigs = data.values.slice(1);
				loading = false;
			})
			.catch((e) => {
				loading = false;
				errorOccured = true;
				console.error(e);
			});
	})
</script>

<main>
	<h1>Upcoming Gigs</h1>
	<hr />
	{#if loading}
		<LoadingSpinner />
	{:else if errorOccured}
		<p>An error occured while fetching data</p>
	{:else}
		{#each gigs as gig (gig)}
			<ListItem artist={gig[0]} venue={gig[1]} date={gig[2]} supports={gig[4]} />
			<hr />
		{/each}
	{/if}
	{#if loading}
		<hr />
	{/if}
	<div class="external-links">
		<ExternalLink label="Past gigs" subLabel="from setlist.fm" link="https://www.setlist.fm/concerts/alexking66" />
		<ExternalLink label="Potential future gigs" subLabel="from SongKick" link="https://www.songkick.com/users/alex-king-47" />
	</div>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		margin: 0 auto;
		color: #ddd;
		background-color: #1A1A1A;
	}

	h1 {
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	.external-links {
		display: flex;
		justify-content: center;
		margin: 3rem 0;
	}
</style>
