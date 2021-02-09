<script>
	export let title;
	export let description;
</script>
<h2>{title}</h2>
<hr />
<p class='description'>{description}</p>

<style>
	hr{
		border-width: 0;
		width:200px;
		height:1px;
		background-color:#FFF200;
	}
	h2{
		margin: 4px 0;
	}
	.description{
		text-transform: uppercase;
		font-size:13px;
		max-width:480px;
		text-align: center;
	}
</style>