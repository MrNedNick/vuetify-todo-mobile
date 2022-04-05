<template>
  <div>
    <v-list-item
      :class="{ 'blue lighten-5': task.done }"
      @click="$store.commit('doneTask', task.id)"
    >
      <template v-slot:default>
        <v-list-item-action>
          <v-checkbox :input-value="task.done" color="primary" />
        </v-list-item-action>

        <v-list-item-content>
          <v-list-item-title
            :class="{ 'text-decoration-line-through': task.done }"
          >
            {{ task.title }}
          </v-list-item-title>
        </v-list-item-content>

        <v-list-item-action>
          <v-btn @click.stop="dialogs.delete = true" icon>
            <v-icon color="primary lighten-1">mdi-delete</v-icon>
          </v-btn>
        </v-list-item-action>
      </template>
    </v-list-item>
    <v-divider></v-divider>

    <dialog-delete v-if="dialogs.delete"/>
  </div>
</template>

<script>
export default {
    props: ['task'],
    data() {
      return {
        dialogs: {
          delete: false
        }
      }
    },
    components: {
      'dialog-delete': require('@/components/Todo/Dialogs/DialogDelete.vue').default
    }
};
</script>
