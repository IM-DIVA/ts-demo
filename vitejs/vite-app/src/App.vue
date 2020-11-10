<template>
	<button @click="toggleModalState">Open modal: {{ isOpen }}</button>
	<modal v-if="isOpen" @close="toggleModalState">
		<p ref="h3Ref">{{ book.title }}</p>
	</modal>
</template>
<script>
import Modal from './components/Modal/Modal.vue';
import { defineComponent, nextTick, onMounted, onUnmounted, onUpdated, reactive, ref } from 'vue';

export default defineComponent({
	components: {
		Modal
	},
	setup(props, context) {
		const h3Ref = ref(null);
		const isOpen = ref(false);
		const book = reactive({ title: 'Book' });
		const toggleModalState = async () => {
			isOpen.value = !isOpen.value;
			await nextTick();
			book.title = (new Date()).toLocaleTimeString();
		};
		onMounted(() => {
			console.log(h3Ref)
			h3Ref.value.style.color = 'red'
			console.log('mounted!');
		});
		onUpdated(() => {
			console.log('updated!');
		});
		onUnmounted(() => {
			console.log('unmounted!');
		});
		return {
			h3Ref,
			isOpen,
			book,
			toggleModalState
		};
	}
});
</script>
<style scoped>
</style>