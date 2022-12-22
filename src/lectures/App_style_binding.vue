<template>
	<div>
		<div :style="styleObejct">
			Lorem ipsum dolor sit amet consectetur adipisicing elit. Deleniti
			inventore laborum consequatur sequi ipsam deserunt nisi assumenda cumque
			commodi corporis quaerat natus saepe dolorem magni, ducimus dolores
			numquam error nobis.
		</div>
		<button v-on:click="minus">-</button>
		<button v-on:click="plus">+</button>
	</div>
</template>

<script>
import { computed, reactive, ref } from 'vue';

export default {
	setup() {
		// const styleObejct = reactive({
		// 	color: 'red',
		// 	fontSize: '13px',
		// });

		const fontSize = ref(13);
		const styleObejct = computed(() => {
			return {
				color: 'red',
				fontSize: `${fontSize.value}px`,
			};
		});

		const minus = () => {
			console.log(fontSize.value);
			fontSize.value--;
		};
		const plus = () => {
			fontSize.value++;
		};
		return {
			styleObejct,
			minus,
			plus,
		};
	},
};
</script>

<style lang="scss" scoped></style>
