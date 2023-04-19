<template>
	<div id="app">
		<h1>Todo aplication</h1>
		<AddTodo v-on:add-todo="addTodo" />
		<hr />
		<!-- Тут мы так же будем прослушивать событие romove-todo, которое было создано в компоненте TodoList в методе removeTodoMethod -->
		<!-- Так же указываем в качестве значения события remove-todo какой-то метод (в нашем случае это будет метод removeTodoMethod), который будет описан в объекте methods -->
		<TodoList v-bind:todosProp="todos" v-on:remove-todo="removeTodoMethod" />
	</div>
</template>

<script>
import TodoList from '@/components/TodoList.vue'
import AddTodo from '@/components/AddTodo.vue'
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
		AddTodo,
	},
	methods: {
		// тут мы описываем метод removeTodoMethod, который указан в качестве значения события remove-todo.
		// когда мы создавали событие remove-todo в компоненте TodoList, то мы так же передали id
		// Далее с помощью метода массивов filter мы просто перезаписываем массив todos
		removeTodoMethod(id) {
			this.todos = this.todos.filter(todosItem => todosItem.id !== id)
		},

		addTodo(todo) {
			this.todos.push(todo)
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
