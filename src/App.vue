<template>
	<div class="main" id="app">
		<TodoList @removeTodo="removeTodo($event)" @changeStatus="changeStatus($event)" :todos="todos" />
	</div>
</template>

<script>
import TodoList from './components/TodoList.vue'

export default {
	name: 'App',
	components: {
		TodoList
	},
	data() {
		return {
			todos: [
				{ name: "First Todo", description: 'this is First Todo', id: 1, isChecked: false, day: '2' },
				{ name: "Second Todo", description: "this is second Todo", id: 2, isChecked: true, day: '1' }
			],
			firstName: "Ali",

		}
	},
	methods: {
		removeTodo(todoId) {
			let todoIndex = this.todos.findIndex(todo => todo.id == todoId)
			this.todos.splice(todoIndex, 1)
		},
		changeStatus(todoId) {
			let todo = this.todos.find(todo => todo.id == todoId)
			todo.isChecked = !todo.isChecked
		}
	}
}
</script>

<style>
* {
	margin: 0;
	padding: 0;
	font-family: "Baloo Bhaijaan 2";
}

body {
	background-color: #fff6d8;
	overflow: hidden;
}

.main {
	margin-top: 60px;
}
</style>
