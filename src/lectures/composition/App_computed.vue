<template>
	<div>
		<h2>{{ teacher.name }}</h2>
		<h3>강의가 있습니까?</h3>
		<!-- <p>{{ teacher.lectures.length > 0 ? '있음' : '없음' }}</p> -->
		<p>{{ hasLecture }}</p>
		<p>{{ hasLecture }}</p>
		<p>{{ exisLecture() }}</p>
		<p>{{ exisLecture() }}</p>
		<button v-on:click="counter++">Counter : {{ counter }}</button>
		<h2>{{ fullName }}</h2>
	</div>
</template>

<script>
import { computed, reactive, ref } from 'vue';

export default {
	setup() {
		const teacher = reactive({
			name: '오영일',
			lectures: ['HTML/CSS', 'JavaScript', 'Vue3'],
		});

		const hasLecture = computed(() => {
			console.log('computed');
			return teacher.lectures.length > 0 ? '있음' : '없음';
		});

		const exisLecture = () => {
			console.log('method');
			return teacher.lectures.length > 0 ? '있음' : '없음';
		};

		const counter = ref(0);

		const firstName = ref('홍');
		const lastName = ref('길동');

		const fullName = computed({
			get() {
				return `${firstName.value} ${lastName.value}`;
			},
			set(value) {
				console.log(value);
				[firstName.value, lastName.value] = value.split('');
			},
		});
		fullName.value = '코딩';
		console.log(fullName.value);
		return {
			teacher,
			hasLecture,
			exisLecture,
			counter,
			fullName,
		};
	},
};
</script>

<style lang="scss" scoped></style>
