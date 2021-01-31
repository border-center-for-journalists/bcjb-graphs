<script>
import VizHeader from '../components/VizHeader.svelte';
import Gauge from '../components/Gauge.svelte';
const headerOpts = {
	title : 'Porcentage de comprobación',
	description : 'Se indican el porcentaje de gastos comprobados mediante facturas en solicitudes de información.'
};


</script>
<VizHeader {...headerOpts} />
<div class='gauges'>
	<Gauge value='33.23' title='Baja California Norte' />
	<Gauge value='33.23' title='Baja California Sur' />
	<Gauge value='33.23' title='Chihuahua' />
	<Gauge value='33.23' title='Coahuila' />
	<Gauge value='33.23' title='Nuevo León' />
	<Gauge value='33.23' title='Sonora' />
	<Gauge value='33.23' title='Tamaulipas' />
</div>
<style>
	.gauges{
		display: flex;
		flex-wrap: wrap;
		max-width: 700px;
		justify-content: space-around;
	}
</style>