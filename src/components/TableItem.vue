<template>
	<tr>
		<td>{{ props.row.name }}</td>
		<td>{{ props.row.itemPrice }}</td>
		<td>{{ props.row.quantity }}</td>
		<td>{{ props.row.totalPrice }}</td>
	</tr>
</template>

<script setup lang="ts">
import type { rowData } from "../types/types";

const props = defineProps<{
	row: rowData;
}>();
</script>

<style lang="scss"></style>
