<template>
    <v-dialog
      :value='true'
      persistent
      max-width="290"
    >
      <v-card>
        <v-card-title class="text-h5">
          Edit task
        </v-card-title>
        <v-card-text>
            Edit the title of this task:
            <v-text-field v-model="taskTitle"/>
        </v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            text
            @click="$emit('close')"
          >
            No
          </v-btn>
          <v-btn
            color="red darken-1"
            text
            @click="$store.dispatch('deleteTask', task.id)"
          >
            Save
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
</template>

<script>
export default {
    props: ['task'],
    data() {
      return {
        taskTitle: null
      }
    },
    mounted() {
      this.taskTitle = this.task.title
    }
}
</script>

<style>

</style>