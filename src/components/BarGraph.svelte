<script>
	import VizHeader from '../components/VizHeader.svelte';
	import Bar from "svelte-chartjs/src/Bar.svelte"


	const headerOpts = {
		title : 'Los montos que no cuadran',
		description : 'Se indican los gastos reportados en los micrositios y por solicitud de información'
	};

	let data = {
		labels: ["BCN*","BCS*","CHI","COAH","NL*","SON*","TAM"],
		datasets: [
		  {
		    label: "Monto Publicado",
		    data: [0,0,3465700000,558240163.22,0,0,990000000],
		    backgroundColor : '#FFF200'
		  },
		  {
		    label: "Monto según solicitud",
		    data: [ 334783549.88,214813097, 234614875.09,262898439.91, 2513872893.00,680271709.32, 990000000.00],
		    backgroundColor : '#D48B4C'
		  },/*
		  {
		    label: "Monto comprobable",
		    data: [200414661.86, 2256852.18, 38861427.78,0,0,35326616,0 ],
		    backgroundColor : '#F73C12'
		  }*/
		]
	};

	let options = {
		tooltips: {
	        callbacks: {
	            label: tooltipItem => '$' + new Intl.NumberFormat().format(tooltipItem.value/1000000) + ' MDP'
	        }
	    },
		responsive: true,
		legend : {
			labels : {
				boxWidth : 15,
				fontFamily : 'Aleo'
			}
		},
		scales: {
		  xAxes: [
		    {
		      gridLines: {
		        display: true,
		        color: ['#666666','#1f1f1f'],
		        drawBorder: true
		      },
		      ticks: {
		        fontColor: '#BCBCBC',
		        fontFamily: 'Aleo',
		        fontSize: 14
		      }
		    }
		  ],
		  yAxes: [
		    {
		      gridLines: {
		        display: true,
		        color: ['#1f1f1f'],
		        drawBorder: true,
		      },
		      ticks: {
		        beginAtZero: true,
		        fontColor: '#BCBCBC',
		        fontFamily: 'Aleo',
		        callback: value => new Intl.NumberFormat().format(value/1000000) + ' MDP',
		      }
		    }
		  ]
		}
	}
</script>
<VizHeader {...headerOpts} />
<div class='container'>
	<Bar data={data} {options} />
	<p><strong>* BCN, BCS, NL y SON no pubicaron activamente el monto total de su gasto en sus sitios oficiales.</strong></p>
</div>
<style>
	.container{
		width: 650px;
		margin: 0 auto;
		height: 600px;
	}
	p{
		font-size: 15px;
		text-align: left;
		color:#999;
	}
</style>