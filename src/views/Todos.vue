<template>
	<div>
		<router-link to="/">Home</router-link>
		<hr />
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
			todos: [],
		}
	},
	components: {
		TodoList,
		AddTodo,
	},
	mounted() {
		fetch('https://jsonplaceholder.typicode.com/todos?_limit=3')
			.then(response => response.json())
			.then(json => {
				this.todos = json
			})
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
