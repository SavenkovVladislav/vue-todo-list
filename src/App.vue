<template>
	<div id="app">
		<h1>Todo aplication</h1>
		<hr />
		<TodoList v-bind:todosProp="todos" v-on:remove-todo="removeTodoMethod" />
	</div>
</template>

<script>
import TodoList from '@/components/TodoList.vue'
export default {
	name: 'App',
	data() {
		return {
			todos: [
				{ id: 1, title: 'title1', completed: false },
				{ id: 2, title: 'title2', completed: false },
				{ id: 3, title: 'title3', completed: false },
			],
		}
	},
	components: {
		TodoList,
	},
	methods: {
		removeTodoMethod(id) {
			this.todos = this.todos.filter(todosItem => todosItem.id !== id)
		},
	},
}
</script>

<style>
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
}
</style>
