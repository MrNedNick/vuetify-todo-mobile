<template>
    <v-list
      class="pt-0"
      flat
    >
      <div
        v-for="task in $store.state.tasks"
        :key="task.id"
      >
        <v-list-item
          :class="{ 'blue lighten-5' : task.done }"
          @click="$store.commit('doneTask', task.id)"
        >
          <template v-slot:default>
            <v-list-item-action>
              <v-checkbox
                :input-value="task.done"
                color="primary"
              />
            </v-list-item-action>

            <v-list-item-content>
              <v-list-item-title
                :class="{ 'text-decoration-line-through' : task.done }"
              >
                {{ task.title }}
              </v-list-item-title>
            </v-list-item-content>

            <v-list-item-action>
              <v-btn 
                @click.stop="$store.commit('deleteTask', task.id)"
                icon
              >
                <v-icon color="primary lighten-1">mdi-delete</v-icon>
              </v-btn>
            </v-list-item-action>

          </template>
        </v-list-item>
        <v-divider></v-divider>
      </div>
    </v-list>
</template>

<script>
export default {

}
</script>

<style>

</style>