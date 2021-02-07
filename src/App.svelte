<script>
	import InfoTable from './components/InfoTable.svelte';
	import RadarGrid from './components/RadarGrid.svelte';
	import BarGraph from './components/BarGraph.svelte';
	import queryString from 'query-string';

	const urlParams = queryString.parse(location.search);
	const table = urlParams.table ? urlParams.table : '1';

	const header1 = {
		title : 'Transparencia Activa de Gasto COVID',
		description : 'Se indica que estados no cuentan con información del gasto COVID en sus sitios oficiales.'
	};


	const table1 = {
		header: [
			{label:''},
			{label:'Estado'},
			{label:'Micrositio'},
			{label:'Commprobantes'},
			{label:'Porcentaje Comprobado'},
		],
		rows: [
			['bcn','Baja California Norte',false,false,.59],
			['bcs','Baja California Sur',false,false,.01],
			['chi','Chihuahua',true,false,.16],
			['coah','Coahuila',true,false,0],
			['nl','Nuevo León',true,false,0],
			['son','Sonora',true,false,.05],
			['tam','Tamaulipas',true,false,0],
		]
	}


	const header2 = {
		title : 'Auditorias y modificaciones a la ley',
		description : ''
	};

	const table2 = {
		header: [
			{label:''},
			{label:'Estado'},
			{label:'Fiscalización Extraordinaria'},
			{label:'Modificaciones en el Congreso'},
		],
		rows: [
			['bcn','Baja California Norte',false,'N/A'],
			['bcs','Baja California Sur',false,'N/A'],
			['chi','Chihuahua',false,'Aprobó reasignaciones sin limtes'],
			['coah','Coahuila',false,'No respondió'],
			['nl','Nuevo León',false,'Aprobó reasignaciones prespuestales'],
			['son','Sonora',true,'Deuda por 1,300 millones'],
			['tam','Tamaulipas',false,'Deuda por 4,600 millones'],
		]
	}

</script>

<main>
	{#if table === '1'}
		<InfoTable data={table1} header={header1}/>
	{:else if table === '2'}
		<RadarGrid />
	{:else if table === '3'}
		<BarGraph />
	{:else if table === '4'}
		<InfoTable data={table2}  header={header2} />
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