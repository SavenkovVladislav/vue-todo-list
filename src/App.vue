<template>
	<div id="app">
		<h1>Todo aplication</h1>
		<!-- Для того, чтобы указать vuejs куда необходимо рендерить нужные страницы необходимо использовать специальный компонент router-view -->
		<router-view />
	</div>
</template>

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
