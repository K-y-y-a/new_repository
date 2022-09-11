<template>
	<main>
		<div class="app-title">to-do list</div>
		<TaskForm @onAddTask="addTask"></TaskForm>
		<ul class="task-list my-list">
			<li v-for="item in taskList" :key="item.id">
				<Task @onRemove="removeTask(item.id)" :model="item"></Task>
			</li>
		</ul>
	</main>	
</template>

<script>
	import TaskForm from "./components/TaskForm.vue"
	import Task from "./components/Task.vue"
	import { ref } from 'vue'

	export default {
		name: 'App',
		components: {
			Task,
			TaskForm
		},
		setup() {
			const taskList = ref( [
				{id:0, description: 'Получилось найти самый подходящий смысловой тег — использовать его.'}, 
				{id:1, description: 'Для потоковых контейнеров — <div>.'}, 
				{id:2, description: 'Для мелких фразовых элементов (слово или фраза) — <span>.'}
			] )
		
			const addTask = ({ description }) => {
				taskList.value = [...taskList.value, {id: taskList.value[taskList.value.length - 1].id + 1, description}]
			}

			const removeTask = (id) => {
      			taskList.value = taskList.value.filter(x => x.id !== id)
    		}

			return {
				taskList,
				addTask,
				removeTask
			}
		}
	}
</script>

<style scoped>
	.task-list {
		list-style: none;
	}

	.app-title{
	    text-align: center;
	    font-size: 46px;
	    font-weight: 600;
	    font-style: italic;
	}
</style>
