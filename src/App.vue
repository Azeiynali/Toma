<template>
	<div class="main" id="app">
		<TodoList v-if="firstName" @addTodoModel="addTodoModel" :firstName="firstName"
			@changeStatus="changeStatus($event)" :todos="todos" />
		<AddBox v-if="firstName" @addTodo="addTodo" ref="AddBox" />
		<LoginBox @deleteLogin="deleteLogin" v-if="!loginShow" @changeName="changeName" />
	</div>
</template>

<script>
function getCookie() {
	try {
		const docCookies = document.cookie;
		const cookiePairs = docCookies.split(";");
		const cookies = {};

		for (const cookiePair of cookiePairs) {
			const [name, value] = cookiePair.split("=");
			cookies[name] = value;
		}

		var webData = cookies['data']
		webData = JSON.parse(webData);
	}
	catch {
		webData = { name: "", todos: [] }
	}

	console.log(webData);
	return webData
}


import TodoList from './components/TodoList.vue'
import AddBox from './components/AddBox.vue'
import LoginBox from './components/LoginBox.vue'

export default {
	name: 'App',
	components: {
		TodoList,
		AddBox,
		LoginBox
	},
	data() {
		return {
			todos: getCookie().todos,
			firstName: getCookie().name,
			loginShow: Boolean(getCookie().name)
		}
	},
	methods: {
		changeStatus(todoId) {
			let todo = this.todos.find(todo => todo.id == todoId)
			this.todos.pop(todo)
			this.setCookie()
		},
		addTodoModel() {
			this.$refs.AddBox.show()
		},
		addTodo(todo) {
			console.log(todo);
			this.todos.push(todo)
			this.setCookie()
		},
		setCookie() {
			const cookie = JSON.stringify({ name: this.firstName, todos: this.todos });
			document.cookie = `data=${cookie}`
		},
		changeName(name) {
			this.firstName = name

			this.setCookie()
		},
		deleteLogin() {
			this.loginShow = true
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
