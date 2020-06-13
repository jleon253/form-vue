<template>
	<div id="app">
		<div class="container my-3">
			<Formulario />
		</div>
	</div>
</template>

<script>
	import Formulario from './components/Formulario.vue'
	export default {
		name: 'App',
		components: {
			Formulario,
		},
	}
</script>

<style>
	#app {
		font-family: Avenir, Helvetica, Arial, sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
	}
	h1,
	h2,
	h3,
	h4,
	h5 {
		font-family: 'Roboto', sans-serif;
	}
</style>
