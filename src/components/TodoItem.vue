<template>
	<div class="todo-item d-flex justify-content-between align-items-center mb-3">
		<div class="form-check">
			<input
				type="checkbox"
				class="form-check-input"
				:checked="todo.completed"
				@change="toggleComplete"
			/>
			<label
				:class="{ 'text-decoration-line-through': todo.completed }"
				class="form-check-label"
				>{{ todo.text }}</label
			>
		</div>
		<button @click="$emit('delete-todo', todo.id)" class="btn btn-danger btn-sm">Delete</button>
	</div>
</template>

<script>
export default {
	props: ["todo"],
	methods: {
		toggleComplete() {
			this.$emit("toggle-complete", this.todo.id);
		},
	},
};
</script>

<style scoped>
.todo-item {
	padding: 15px;
	border-radius: 15px;
	background: #444;
	color: #fff;
	box-shadow: 0 6px 12px rgba(0, 0, 0, 0.1);
	transition: transform 0.2s ease;
	border: 1px solid #00bcd4;
}
.todo-item:hover {
	transform: scale(1.05);
}
.todo-item .text-decoration-line-through {
	text-decoration: line-through;
}
</style>

<!-- Add this link to main index.html or App.vue to avoid adding it in each component -->
<link
	rel="stylesheet"
	href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.min.css"
/>
