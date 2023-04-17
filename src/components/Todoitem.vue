<template>
	<li>
		<span v-bind:class="{ done: todoProp.completed }">
			<input
				type="checkbox"
				v-on:change="todoProp.completed = !todoProp.completed"
			/>
			<strong>{{ todoProp.id }}</strong>
			{{ todoProp.title }}
		</span>
		<button v-on:click="$emit('remove-todo', todoProp.id)">&times;</button>
	</li>
</template>

<script>
export default {
	props: ['todoProp'],
}
</script>

<style scoped>
li {
	border: 1px solid #ccc;
	display: flex;
	justify-content: space-between;
	padding: 0.5rem 2rem;
	margin-bottom: 1rem;
}

input {
	margin-right: 1rem;
}
.done {
	text-decoration: line-through;
}
</style>
