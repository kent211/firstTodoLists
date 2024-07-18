<template>
	<div class="add-todo input-group mb-3">
		<input
			v-model="newTodo"
			@keyup.enter="addTodo"
			placeholder="Add a new task"
			class="form-control"
		/>
		<div class="input-group-append">
			<button @click="addTodo" class="btn btn-cyan">Add</button>
		</div>
	</div>
</template>

<script>
export default {
	data() {
		return {
			newTodo: "",
		};
	},
	methods: {
		addTodo() {
			if (this.newTodo.trim() !== "") {
				this.$emit("add-todo", this.newTodo.trim());
				this.newTodo = "";
			}
		},
	},
};
</script>

<style scoped>
.add-todo {
	margin-bottom: 20px;
}
.add-todo input {
	background-color: #333;
	color: #fff;
	border-top-left-radius: 20px;
	border-bottom-left-radius: 20px;
	box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
	border: 1px solid #00bcd4;
}
.add-todo button {
	border-top-right-radius: 20px;
	border-bottom-right-radius: 20px;
	box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
	border: 1px solid #00bcd4;
}
.btn-cyan {
	background-color: #00bcd4;
	color: #fff;
}
.btn-cyan:hover {
	background-color: #0097a7;
}
.add-todo input::placeholder {
	color: #fff;
}
</style>
