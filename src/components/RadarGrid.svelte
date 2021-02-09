<script>
import VizHeader from '../components/VizHeader.svelte';
import Gauge from '../components/Gauge.svelte';
const headerOpts = {
	title : 'Poco gasto comprobado',
	description : 'En solicitudes de información los estados respaldaron muy poco de sus gastos con comprobantes fiscales.'
};


</script>
<VizHeader {...headerOpts} />
<div class='gauges'>
	<Gauge value='59.86' title='Baja California Norte' />
	<Gauge value='1.05' title='Baja California Sur' />
	<Gauge value='16.56' title='Chihuahua' />
	<Gauge value='0' title='Coahuila' />
	<Gauge value='0' title='Nuevo León' />
	<Gauge value='5.19' title='Sonora' />
	<Gauge value='0' title='Tamaulipas' />
</div>
<style>
	.gauges{
		display: flex;
		flex-wrap: wrap;
		max-width: 650px;
		justify-content: space-around;
	}
</style>