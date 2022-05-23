<template>
	<div class="app">
		<Table />
	</div>
</template>

<script setup lang="ts">
import Table from "./components/TableComponent.vue";
</script>

<style lang="scss">
.app {
	width: 100vw;
	height: 100vh;
	overflow-x: hidden;
	background: rgb(2, 0, 36);
	background: linear-gradient(
		90deg,
		rgba(2, 0, 36, 1) 0%,
		rgba(255, 255, 255, 1) 0%,
		rgba(0, 86, 255, 0.5942752100840336) 93%
	);
}
</style>
