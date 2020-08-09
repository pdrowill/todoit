<template>
  <v-card
			class="mx-auto mt-10"
			max-width="70%"
		>
			<v-card-title>
				Completed tasks
			</v-card-title>
      <v-card-subtitle>
				Completed To Do's are deleted after 30 days
			</v-card-subtitle>
      
			<v-card-text>
				<v-card
					outlined 
					class="mb-3"
					v-for="(completedTask, index) in completedTasks" 
					:key="index"
				>
					<div class="d-flex" >
						<div>
							<v-card-title> {{completedTask.title}} </v-card-title>
							<!-- <v-card-subtitle> {{task.subtitle}} </v-card-subtitle> -->
						</div>
						<v-spacer></v-spacer>
						<div class="d-flex">
							<v-btn 
								icon
								class="align-self-center mr-5"
								color="deep-purple darken-1"
								@click="$emit('reverted-task', completedTask)"
							>
								<v-icon>mdi-backup-restore</v-icon>
							</v-btn>
							<v-btn 
								icon
								class="align-self-center mr-5"
								color="red"
								@click="$emit('task-deleted', completedTask)"
							>
								<v-icon>mdi-close</v-icon>
							</v-btn>
						</div>
					</div>
				</v-card>
			</v-card-text>

		</v-card>
</template>

<script>
export default {
  props: {
		completedTasks: {
			type: Array,
			required: true
		}
	}
}
</script>

<style>

</style>