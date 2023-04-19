<template>
	<div>
		<ul>
			<!-- Тут мы будем обрабатывать/прослушивать событие remove-todo, которое было создано в дочернем компоненте TodoItem -->
			<!-- Делается это с помощью дериктивы v-on, где указывается название того события, которое мы описали в TodoItem. Данное событие называется remove-todo -->
			<!-- В качестве значения v-on:remove-todo необходимо указать метод, который будет выполняться. Назовем его removeTodoMethod и опишем в объекте methods-->
			<TodoItem
				v-for="(todo, index) in todosProp"
				v-bind:todoProp="todo"
				v-bind:todoIndex="index"
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
		// Тут создается метод removeTodoMethod, который будет выполняться при прослушивании события remove-todo
		// Так как в компоненте TodoItem в событие remove-todo мы передали данные, а именно свойство id, то тут мы можем вытащить этот id
		// Далее мы создаем новое событие, которое передать теперь уже в компонент app и называем его также remove-todo, назвать его можно как угодно
		// В целом у нас повторяется история с тем, как мы передавали событие из TodoItem в TodoList, только теперь мы хотим передать событие с данными из TodoList в App
		removeTodoMethod(id) {
			console.log(id)
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
