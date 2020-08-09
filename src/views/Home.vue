<template>
  <div class="home">
    <NewTask @taskAdded="addTask" />
    <TaskProgress :progress="progress" />
    <Todos :tasks="tasks" @task-completed="completeTask" />
    <CompletedTasks :completedTasks="completedTasks" @task-deleted="deleteTask" @reverted-task="revertTask" />
  </div>
</template>

<script>
// @ is an alias to /src
import NewTask from '@/components/NewTask.vue'
import TaskProgress from '@/components/TaskProgress.vue'
import Todos from '@/components/Todos.vue'
import CompletedTasks from '@/components/CompletedTasks.vue'

export default {
  name: 'Home',
  data() {
    return {
      // expected object { title: 'Read a comic', pending: true},
      tasks: [],
      completedTasks: []
    }
  },
  computed: {
    progress() {
      const total = this.tasks.length + this.completedTasks.length
      const done = this.completedTasks.length
      if(this.completedTasks.length > 0) {
        return done / total * 100
      }
      else {
        return 0
      }
    }
  },
  watch: {
      tasks: {
        deep: true,
        handler() {
          localStorage.setItem('tasks', JSON.stringify(this.tasks))
        }
      },
      completedTasks: {
        deep: true,
        handler() {
          localStorage.setItem('completedTasks', JSON.stringify(this.completedTasks))
        }
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
    completeTask(index) {
      this.tasks.splice(index, 1)

      this.completedTasks.push ({
        title: index.title,
        pending: false
      })
    },
    deleteTask(index) {
      this.completedTasks.splice(index, 1)
    },
    revertTask(index) {
      this.completedTasks.splice(index, 1)

      this.tasks.push ({
        title: index.title,
        pending: false
      })
    }
  },
  components: {
    NewTask,
    TaskProgress,
    Todos,
    CompletedTasks
  },
  created() {
    const jsonTasks = localStorage.getItem('tasks')
    const arrayTasks = JSON.parse(jsonTasks)
    this.tasks = Array.isArray(arrayTasks) ? arrayTasks : []
    
    const jsonCompletedTasks = localStorage.getItem('completedTasks')
    const arrayCompletedTasks = JSON.parse(jsonCompletedTasks)
    this.completedTasks = Array.isArray(arrayCompletedTasks) ? arrayCompletedTasks : []
    }
  
}
</script>
