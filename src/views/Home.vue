<template>
  <div class="home">
    <NewTask @taskAdded="addTask" />
    <Todos :tasks="tasks" @task-deleted="deleteTask" />
    <CompletedTasks :completedTasks="completedTasks" />
  </div>
</template>

<script>
// @ is an alias to /src
import NewTask from '@/components/NewTask.vue'
import Todos from '@/components/Todos.vue'
import CompletedTasks from '@/components/CompletedTasks.vue'

export default {
  name: 'Home',
  data() {
    return {
      // expected object { title: 'Read a comic', pending: true},
      tasks: [],
      completedTasks: [{ title: 'Completed', pending: true},]
    }
  },
  methods: {
    addTask(newTask) {
      if(newTask.task) {
        this.tasks.push ({
          title: newTask.task,
          pending: true
        })
      }
    },
    deleteTask(index) {
      this.tasks.splice(index, 1)
    }
  },
  components: {
    Todos, 
    NewTask,
    CompletedTasks
  },
  
}
</script>
