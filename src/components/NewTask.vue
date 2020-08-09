<template>
  <div class="new-task mx-auto mt-10">
    <v-text-field
      label="Add New Task"
      color="deep-purple darken-1"
      outlined
      v-model="task"
      type="text"
      @keydown.enter="add"
      required
    ></v-text-field>
  </div>
</template>

<script>
export default {
  data() {
    return {
      task: ''
    }
  },
  methods: {
    add() {
      this.$emit('taskAdded', {task: this.task})
      this.task = ''
    }
  },
}
</script>

<style scoped>
  .new-task {
    max-width: 70%;
  }
</style>