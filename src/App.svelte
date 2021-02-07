<script>
	import InfoTable from './components/InfoTable.svelte';
	import RadarGrid from './components/RadarGrid.svelte';
	import BarGraph from './components/BarGraph.svelte';
	import queryString from 'query-string';

	const urlParams = queryString.parse(location.search);
	const table = urlParams.table ? urlParams.table : '1';

</script>

<main>
	{#if table === '1'}
		<InfoTable />
	{:else if table === '2'}
		<RadarGrid />
	{:else if table === '3'}
		<BarGraph />
	{/if}
</main>

<style>
	main{
		display: flex;
		justify-content: center;
		align-items: center;
		flex-direction: column;
		padding-top:40px;
	}
	
</style>