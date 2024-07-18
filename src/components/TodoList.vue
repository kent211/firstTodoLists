<template>
	<div class="todo-list container mt-5">
		<AddTodo @add-todo="addTodo" />
		<TodoItem
			v-for="todo in todos"
			:key="todo.id"
			:todo="todo"
			@delete-todo="deleteTodo"
			@toggle-complete="toggleComplete"
		/>
	</div>
</template>

<script>
import AddTodo from "./AddTodo.vue";
import TodoItem from "./TodoItem.vue";

export default {
	components: { AddTodo, TodoItem },
	data() {
		return {
			todos: JSON.parse(localStorage.getItem("todos")) || [],
		};
	},
	methods: {
		addTodo(text) {
			const newTodo = {
				id: Date.now(),
				text,
				completed: false,
			};
			this.todos.push(newTodo);
			this.saveTodos();
		},
		deleteTodo(id) {
			this.todos = this.todos.filter((todo) => todo.id !== id);
			this.saveTodos();
		},
		toggleComplete(id) {
			const todo = this.todos.find((todo) => todo.id === id);
			if (todo) {
				todo.completed = !todo.completed;
				this.saveTodos();
			}
		},
		saveTodos() {
			localStorage.setItem("todos", JSON.stringify(this.todos));
		},
	},
};
</script>

<style scoped>
.todo-list {
	max-width: 600px;
	margin: 0 auto;
	background: #222;
	border-radius: 15px;
	box-shadow: 0 6px 12px rgba(0, 0, 0, 0.1);
	padding: 20px;
	border: 1px solid #00bcd4;
}
</style>
