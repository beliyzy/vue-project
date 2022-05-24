<template>
	<div class="wrapper">
		<button @click="generateData()">Сгенерировать</button>
		<div v-if="tableData.length" class="container">
			<table border="1">
				<thead>
					<td>Наименование</td>
					<td>Цена</td>
					<td>Количество</td>
					<td>Стоимость</td>
				</thead>
				<TableItem v-for="(row, index) in tableData" :key="index" :row="row" />
			</table>
			<div class="total-price">
				Итоговая стоимость: {{ resultSum.toFixed(2) }}
			</div>
		</div>
	</div>
</template>

<script setup lang="ts">
import { reactive, ref } from "vue";
import TableItem from "./TableItem.vue";
import type { rowData } from "../types/types";

const alphabet = [
	"а",
	"б",
	"в",
	"г",
	"д",
	"е",
	"ё",
	"ж",
	"з",
	"и",
	"й",
	"к",
	"л",
	"м",
	"н",
	"о",
	"п",
	"р",
	"с",
	"т",
	"у",
	"ф",
	"х",
	"ц",
	"ч",
	"ш",
	"щ",
	"ъ",
	"ы",
	"ь",
	"э",
	"ю",
	"я",
];

let tableData: rowData[] = reactive([]);
let resultSum = ref(0);

function generateWord(value: string) {
	for (let j = 0; j < 5; j++) {
		value = value + alphabet[Math.floor(Math.random() * alphabet.length)];
	}
	return value;
}
function generateData() {
	tableData.length = 0;
	for (let i = 0; i < 50; i++) {
		let name = generateWord("");
		let itemPrice = Number((Math.random() * 1000).toFixed(2));
		let quantity = Math.floor(Math.random() * 100 + 1);
		let totalPrice = Number((itemPrice * quantity).toFixed(2));

		tableData.push({
			name,
			itemPrice,
			quantity,
			totalPrice,
		});
	}
	resultSum.value = tableData.reduce((sum, current) => {
		return sum + current.totalPrice;
	}, 0);
}
</script>

<style lang="scss">
table {
	border-spacing: 0;
	width: 100%;
	text-align: center;
	background: #fff;
}
.container {
	width: 100%;
}
button {
	width: 300px;
	margin-bottom: 100px;
	height: 50px;
	border-radius: 30px;
	color: #fff;
	background: #344ccc;
	transition: all 0.3s;
	cursor: pointer;
	&:hover {
		background: #4563ff;
	}
}

.wrapper {
	padding: 100px;
	display: flex;
	flex-direction: column;
	justify-content: center;
	align-items: center;
}

.total-price {
	align-self: flex-end;
	margin-top: 30px;
}
</style>
