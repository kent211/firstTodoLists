<template>
	<div class="home text-center">
		<h1 class="mb-4">Vue.js To-Do List</h1>
		<TodoList />
	</div>
</template>

<script>
import TodoList from "@/components/TodoList.vue";

export default {
	name: "HomeView",
	components: { TodoList },
};
</script>

<style scoped>
.home {
	text-align: center;
	margin-top: 50px;
	color: #fff;
}
.home h1 {
	font-size: 2.5rem;
	color: #00bcd4;
}
</style>
