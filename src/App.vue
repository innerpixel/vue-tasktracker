<template>
	<div class="container">
		<Header 
			@toggle-add-task="toggleAddTask" 
			title="Task Traker" 
			:show-add-task="showAddTask"
		/>	
		<div v-if="showAddTask">
			<AddTask @add-task="addTask"/>
		</div>
		<Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks" />
	</div>
</template>

<script>
import Header from './components/Header' 
import Tasks from './components/Tasks' 
import AddTask from './components/AddTask' 

export default {
	name: 'App',
	components: {
		Header,
		Tasks,
		AddTask
	},
	data() {
		return {
			showAddTask: false, 
			tasks: []
		}
	}, 
	methods: {
		toggleAddTask(){
			this.showAddTask = !this.showAddTask 
		},
		addTask(task){
			this.tasks = [...this.tasks, task]
		},
		deleteTask(id){
			this.tasks = this.tasks.filter( (task) => task.id !== id )
			// console.log('task', id)
		},
		toggleReminder(id) {
			this.tasks = this.tasks.map((task) => task.id === id ? {...task, reminder: !task.reminder } : task )
		}
	}, 
	created(){
	  	this.tasks = [
		{
			id: 1, 
			text: 'Learn Vue js', 
			day: 'March 2nd at 13:00pm', 
			reminder: true
		}, 
		{
			id: 2, 
			text: 'Some more VueJS', 
			day: 'March 2nd at 14:00pm', 
			reminder: true
		}, 
		{
			id: 3, 
			text: 'Be proficient with VUEJS ', 
			day: 'March 2nd at 15:00pm', 
			reminder: false
		}, {
			id: 4, 
			text: 'Expand your VUEJS knowledge', 
			day: 'March 2nd at 16:00pm', 
			reminder: true
		}]
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: 'Poppins', sans-serif;
}
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: flex;
  background: #000;
  color: #fff;
  border: none;
  min-width: 100px;
  text-align : center;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>