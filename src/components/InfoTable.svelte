<script>
	import VizHeader from '../components/VizHeader.svelte';
	const header = {
		title : 'Transparencia Activa de Gasto COVID',
		description : 'Se indica que estados no cuentan con información del gasto COVID en sus sitios oficiales.'
	};
	const table = {
		header: [
			{label:''},
			{label:'Estado'},
			{label:'Micrositio',tooltip:'some text yow'},
			{label:'Commprobantes',tooltip:'some text yow'},
			{label:'Porcentaje Comprobado',tooltip:'some text yow'},
		],
		rows: [
			['bcn','Baja California Norte',true,false,.8],
			['bcs','Baja California Sur',true,false,.8],
			['chi','Chihuahua',true,false,.8],
			['coah','Coahuila',true,false,.7],
			['nl','Nuevo León',true,false,.34],
			['son','Sonora',true,false,0],
			['tam','Tamaulipas',true,false,.8],
		]
	}

</script>
<VizHeader {...header} />
<table>
	<tr>
		{#each table.header as header}
			<th>
				{header.label}
				{#if header.tooltip}
					<span class='tooltip'></span>
				{/if}
			</th>
		{/each}
	</tr>
	{#each table.rows as row}
		<tr>
			{#each row as cell,i}
				{#if i === 0}
					<td><span class='shld {cell}'></span></td>
				{:else if typeof(cell) === 'string'}
					<td>{cell}</td>
				{:else if typeof(cell) === 'boolean'}
					<td><span class='icon {cell}'></span></td>
				{:else if typeof(cell) === 'number'}
					<td><span class='percent-bar' ><span style='width: {cell * 100}%'></span></span></td>
				{/if}
			{/each}
		</tr>
	{/each}
</table>
<style>
	table{
		border-collapse: collapse;
	}
	table tr:first-child th{
		border-top: 0;
		text-align: left;
	}
	table tr td:first-child, table tr th:first-child{
		border-left:0;
		border-right:0;
	}
	table tr td:last-child, table tr th:last-child{
		border-right:0;
	}
	table tr td:nth-child(2),table tr th:nth-child(2){
		border-left:0;
	}
	td,th{
		padding:10px;
		border: 1px solid white;
	}
	th{
		background-color: #343434;
		font-weight: normal;
	}
	td .icon{
		display: block;
		width:17px;
		height:17px;
		margin:0 auto;
	}
	td .false{
		background-image: url('/img/cross.png');
	}
	td .true{
		background-image: url('/img/check.png');
		width:21px;
	}

	td .shld{
		display: block;
		width:30px;
		height:30px;
		float:left;
		margin-right:14px;
	}
	.tooltip{
		background-image: url(/img/info.png);
		width:16px;
		height: 16px;
		display: block;
		float:right;
		position: relative;
		margin:1px 0 0 7px;
	}
	.percent-bar{
		width: 100%;		
		background-color: #343434;
		display: block;
		height:6px;
	}
	.percent-bar span{		
		background-color: #FFF200;
		display: block;
		height:6px;
	}
	.bcn{background-image:url(/img/bcn-shld.png);}
	.bcs{background-image:url(/img/bcs-shld.png);}
	.chi{background-image:url(/img/chi-shld.png);}
	.coah{background-image:url(/img/coah-shld.png);}
	.nl{background-image:url(/img/nl-shld.png);}
	.son{background-image:url(/img/son-shld.png);}
	.tam{background-image:url(/img/tam-shld.png);}

</style>