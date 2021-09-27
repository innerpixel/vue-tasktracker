<template>
<header>
	<h2> {{ title }}</h2>
	<Button 
		@btn-clicked="$emit('toggle-add-task')" 
		:text="showAddTask ? 'Close' : 'Add Task'" 
		:color="showAddTask ? 'red' : 'blue'" /> 
</header>
</template>
 
<script>
import Button from "./Button.vue" ;

export default {

	name: 'Header', 
	props: {
		title: String, 
		showAddTask: Boolean
	},
	components:{
		Button, 
	}
}
</script>

<style scoped>
*{
	display:flex; 
	justify-content: space-between ;
	align-items: center;
	margin-bottom: 20px;
}
</style>

