<template>
	<div>
		<ul>
			<TodoItem
				v-for="todo in todosProp"
				v-bind:todoProp="todo"
				v-on:remove-todo="removeTodoMethod"
			/>
		</ul>
	</div>
</template>

<script>
import TodoItem from '@/components/Todoitem.vue'
export default {
	props: ['todosProp'],
	components: {
		TodoItem,
	},
	methods: {
		removeTodoMethod(id) {
			this.$emit('remove-todo', id)
		},
	},
}
</script>

<style scoped>
ul {
	list-style: none;
	margin: 0;
	padding: 0;
}
</style>
