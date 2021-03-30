<template>
  <div class="home">

    <v-text-field
      v-model="newTaskTitle"
      @click:append="addTaskHandler"
      @keyup.enter="addTaskHandler"
      class="pa-2"
      outlined
      label="Add Task"
      append-icon="mdi-plus"
      hide-details
      clearable
    ></v-text-field>

    <v-list
      v-if="$store.state.tasks.length"
      class="pt-0"
      flat
    >
      <div
        v-for="task in $store.state.tasks"
        :key="task.id"
      >
        <v-list-item
          @click="$store.commit('doneTask', task.id)"
          :class="{ 'blue lighten-5' : task.done }"
        >
          <template v-slot:default>
            <v-list-item-action>
              <v-checkbox :input-value="task.done"></v-checkbox>
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
                <v-icon color="grey lighten-1">mdi-delete</v-icon>
              </v-btn>
            </v-list-item-action>
          </template>
        </v-list-item>
        <v-divider></v-divider>
      </div>
    </v-list>

    <div
      class="no-tasks"
      v-else
    >
      <v-icon
        size="100"
        color='primary'
      >
        mdi-check
      </v-icon>
      <div class="text-h5 primary--text">No Tasks</div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'Todo',
  data() {
    return {
      newTaskTitle: '',
      
    }
  },
  methods: {
    addTaskHandler() {
      this.$store.commit('addTask', this.newTaskTitle)
      this.newTaskTitle = ''
    }
  }
}
</script>

<style lang="sass">
  .no-tasks
    position: absolute
    left: 50%
    top: 50%
    transform: translate(-50%, -50%)
    opacity: 0.5
</style>
