<template>
	<div id="app">
		<router-view></router-view>
	</div>
</template>

<script>
	export default {
		name: 'app'
	}
</script>

<style>
	body{
		margin: 0;
	}
	#app {
		width: 100vw;
		height: 100vh;
		overflow: hidden;
	}
	.index{
		width: 100%;
		height: 100%;
	}
</style>
