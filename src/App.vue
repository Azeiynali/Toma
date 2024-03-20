<template>
	<div class="main" id="app">
		<TodoList @addTodo="addTodoModel" :firstName="firstName" @removeTodo="removeTodo($event)"
			@changeStatus="changeStatus($event)" :todos="todos" />
		<AddBox ref="AddBox" />
	</div>
</template>

<script>
import TodoList from './components/TodoList.vue'
import AddBox from './components/AddBox.vue'

export default {
	name: 'App',
	components: {
		TodoList,
		AddBox
	},
	data() {
		return {
			todos: [
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
		},
		addTodoModel() {
			this.$refs.AddBox.show()
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
	background-color: #fff4ce;
	overflow-x: hidden;
}

.main {
	margin-top: 60px;
}
</style>
