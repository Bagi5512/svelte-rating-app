<script>
	import AddEntry from './AddEntry.svelte';
	import Entry from './Entry.svelte';

	let entries = [];

	let onAddEntry = (event) => {
		let newEntry = event.detail;
		entries = [...entries, newEntry];
	};

	let onRemoveEntry = (event) => {
		entries = entries.filter(entry => entry !== event.detail);
	};

</script>

<div class="main">
	<header>Professor Rating App</header>

	<p>New rating</p>
	<AddEntry on:addentry={onAddEntry}/>

	{#if entries.length === 0}
		<p>No ratings</p>
	{:else}
		<p>Ratings</p>
		{#each entries as entry}
    		<Entry on:removeentry={onRemoveEntry} entry={entry}/>
		{/each}
	{/if}
</div>

<style>
	* {
		margin: 0;
		padding: 0;
		border: 0;
	}
	
	.main {
		max-width: 500px;
		height: 100%;
		background-color: lightblue;
		display: flex;
		flex-direction: column;
		padding-left: 16px;
		padding-right: 16px;
	}

	.main header {
		height: 64px;
		font-size: 24px;
		display: flex;
		align-items: center;
		justify-content: center;
		margin-bottom: 16px;
	}

	.main p {
		display: flex;
		align-items: center;
		justify-content: center;
	}
</style>
