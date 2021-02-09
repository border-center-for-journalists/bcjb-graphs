<script>
	import VizHeader from '../components/VizHeader.svelte';
	export let data;
	export let header;
</script>
<VizHeader {...header} />
<table>
	<tr>
		{#each data.header as header}
			<th>
				{header.label}
				{#if header.tooltip}
					<span class='tooltip'><span class='content'>{header.tooltip}</span></span>
				{/if}
			</th>
		{/each}
	</tr>
	{#each data.rows as row}
		<tr>
			{#each row as cell,i}
				{#if i === 0}
					<td><span class='shld {cell}'></span></td>
				{:else if typeof(cell) === 'string'}
					<td>{cell}</td>
				{:else if typeof(cell) === 'boolean'}
					<td><span class='icon {cell}'></span></td>
				{:else if typeof(cell) === 'number'}
					<td>
						<span class='percent-bar' >
							<span class='bar' style='width: {cell * 100}%'></span>
							<span class='label' >{cell*100}%</span>
						</span>
					</td>
				{/if}
			{/each}
		</tr>
	{/each}
</table>
{#if data.notes}
<p class='notes'>{@html data.notes}</p>
{/if}
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
		font-size:15px;
	}
	.tooltip .content{
		display: block;
		position: absolute;
		top: -6px;
		transform: translateY(-110%) translateX(-50%);
		background-color: black;
		padding: 13px;
		border-radius: 5px;
		min-width: 250px;
		margin-left:7px;
		display: none;
	}
	.tooltip:hover .content{
		display: block;
	}
	.tooltip .content:after{
		content: '';
		display: block;
		width: 0; 
		height: 0; 
		border-left: 10px solid transparent;
		border-right: 10px solid transparent;
		border-top: 10px solid #000;
		position: absolute;
		bottom:-10px;
		left: 50%;
		margin-left:-10px;
	}
	.percent-bar{
		width: 100%;		
		background-color: #343434;
		display: block;
		height:6px;
		position: relative;
	}
	.percent-bar .label{
		position: absolute;
		top:-13px;
		display: block;
		background-color:white;
		color:black;
		border-radius:50%;
		width:30px;
		line-height: 30px;
		font-size:12px;
		text-align: center;
		margin-left:-15px;
		left:50%;
		display: none;

	}
	td:hover .label{
		display: block;
	}
	.percent-bar .bar{		
		background-color: #FFF200;
		display: block;
		height:6px;
	}

	.notes{
		max-width: 716px;
		text-align: left;
		font-size:14px;
	}
	.bcn{background-image:url(/img/bcn-shld.png);}
	.bcs{background-image:url(/img/bcs-shld.png);}
	.chi{background-image:url(/img/chi-shld.png);}
	.coah{background-image:url(/img/coah-shld.png);}
	.nl{background-image:url(/img/nl-shld.png);}
	.son{background-image:url(/img/son-shld.png);}
	.tam{background-image:url(/img/tam-shld.png);}

</style>