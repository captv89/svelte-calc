<script>
	import Calculator from './components/Calculator.svelte';
</script>

<svelte:head>
	<!-- Fonts --><link
		rel="stylesheet"
		href="https://fonts.googleapis.com/icon?family=Material+Icons"
	/>
	<link
		rel="stylesheet"
		href="https://fonts.googleapis.com/css?family=Roboto:300,400,500,600,700"
	/>

	<!-- Pixel Font -->
	<link rel="preconnect" href="https://fonts.googleapis.com" />
	<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
	<link
		href="https://fonts.googleapis.com/css2?family=VT323&display=swap"
		rel="stylesheet"
	/>

	<!-- Material Typography --><link
		rel="stylesheet"
		href="https://unpkg.com/@material/typography@13.0.0/dist/mdc.typography.css"
	/>

	<!-- SMUI --><link
		rel="stylesheet"
		href="https://unpkg.com/svelte-material-ui/bare.css"
	/>

	<style>
		body {
			background: #272828;
			height: 100vh;
			overflow: hidden;
		}
	</style>
</svelte:head>

<Calculator />
