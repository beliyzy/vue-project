<template>
	<tr>
		<td>{{ props.row.name }}</td>
		<td>{{ props.row.itemPrice }}</td>
		<td>{{ props.row.quantity }}</td>
		<td>{{ props.row.totalPrice }}</td>
	</tr>
</template>

<script setup lang="ts">
export interface IRowData {
	name: string;
	itemPrice: number;
	quantity: number;
	totalPrice: number;
}

const props = defineProps<{
	row: IRowData;
}>();
</script>

<style lang="scss"></style>

PROPS { name: '' price '' quantity totalPrice }
