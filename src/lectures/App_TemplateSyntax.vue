<template>
	<div>
		<h2>보건법</h2>
		<P>{{ counter }}</P>
		<p v-once>{{ counter }}</p>
		<p v-once>{{ message }}</p>
		<p>{{ message }}</p>
		<h2>HTML</h2>
		<p>{{ rawHtml }}</p>
		<p v-html="rawHtml"></p>
		<button v-on:click="increment">click!</button>
		<button v-on:click="message = message + '!'">click2!</button>
		<h2>속성 바인딩</h2>
		<div :title="dynamicTitle">마우스를 올려보세요</div>
		<input type="text" value="홍길동" v-bind:disabled="isInputDisabled" />
		<input v-bind="attrs" />
		<h2>JavaScript</h2>
		{{ message.split('').reverse().join('') }}<br />
		{{ isInputDisabled ? 'yes' : 'no' }}
	</div>
</template>

<script>
import { ref } from 'vue';

export default {
	setup() {
		const counter = ref(0);
		const increment = () => {
			counter.value++;
		};
		const message = ref('Hello Vue3');
		const rawHtml = ref('<strong>안녕하세요</strong>');
		const dynamicTitle = ref('안녕하세용!');
		const isInputDisabled = ref(false);
		const attrs = ref({
			type: 'password',
			value: '12345678',
			disabled: false,
		});

		return {
			counter,
			message,
			rawHtml,
			increment,
			dynamicTitle,
			isInputDisabled,
			attrs,
		};
	},
};
</script>

<style lang="scss" scoped></style>
