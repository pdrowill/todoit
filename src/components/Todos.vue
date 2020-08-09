<template>
  <div class="todos">
    <v-card
			class="mx-auto"
			max-width="70%"
		>
			<v-card-title>
				Tasks
			</v-card-title>
			<v-card-subtitle>
				These are your To Do's
			</v-card-subtitle>
      <v-card-text>
        <Task 
          v-for="(task, index) in tasks" 
          :key="index" 
          :task="task" 
          @task-deleted="$emit('task-deleted', index)"
        />
      </v-card-text>
      
		</v-card>
  </div>
</template>

<script>
import Task from '@/components/Task.vue'
export default {
  props: {
    tasks: {
      type: Array,
      required: true
    }
  },
  components: {
    Task
  },
}
</script>

<style>

</style>