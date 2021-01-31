<script>
	import InfoTable from './components/InfoTable.svelte';
	import RadarGrid from './components/RadarGrid.svelte';
	import queryString from 'query-string';

	const urlParams = queryString.parse(location.search);
	const table = urlParams.table ? urlParams.table : 1;

</script>

<main>
	<!-- <InfoTable />  -->
	<RadarGrid />
</main>

<style>
	main{
		display: flex;
		justify-content: center;
		align-items: center;
		flex-direction: column;
	}
	
</style>