<template>
  <div class="task-progress">
    <v-card class="mx-auto mt-1 mb-5" max-width="70%">
      <v-progress-linear :value="progress" color="deep-purple darken-1"></v-progress-linear>
    </v-card>
  </div>
</template>

<script>
export default {
  props: {
    progress: {
      type: Number,
      default: 0
    }
  },
  created() {
    console.log(this.progress)
  }
}
</script>

<style>

</style>