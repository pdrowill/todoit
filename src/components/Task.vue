<template>
	<div class="task">
    <v-card 
      outlined 
      class="mb-3"
    >
			<div class="d-flex">
				<div>
					<v-card-title> {{task.title}} </v-card-title>
					<!-- <v-card-subtitle> {{task.subtitle}} </v-card-subtitle> -->
				</div>
				<v-spacer></v-spacer>
				<div class="d-flex">
					<v-btn 
						icon
						class="align-self-center mr-5"
						color="deep-purple darken-1"
						@click="$emit('task-deleted', task)"
					>
						<v-icon>mdi-check</v-icon>
					</v-btn>
				</div>
			</div>
    </v-card>
  </div>
</template>

<script>
export default {
	props: {
		task: {
			type: Object,
			required: true
		}
	},
	computed: {
		stateClass() {
			return {
				done: this.task.pending
			}
		}
	},
}
</script>

<style>
</style>