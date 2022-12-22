<template>
	<div>
		<div
			class="text"
			:class="[isActvie ? 'active-class' : 'class', errorClass]"
		>
			텍스트 입니다.
		</div>
		<button v-on:click="toggle">toggle</button>
		<button
			v-on:click="classObject['text-danger'] = !classObject['text-danger']"
		>
			toggleError
		</button>
	</div>
</template>

<script>
import { ref, reactive, computed } from 'vue';

export default {
	setup() {
		const isActvie = ref(true);
		const hasError = ref(false);
		// const classObject = reactive({
		// 	active: true,
		// 	'text-danger': true,
		// });

		const classObject = computed(() => {
			return {
				active: true,
				'text-danger': true,
			};
		});

		const activeClass = ref('active');
		const errorClass = ref('error');

		const toggle = () => {
			classObject.value.active = !classObject.value.active;
		};

		return {
			isActvie,
			toggle,
			hasError,
			classObject,
			activeClass,
			errorClass,
		};
	},
};
</script>

<style scoped>
.active {
	font-weight: 900;
}
.text-danger {
	color: red;
}
</style>
