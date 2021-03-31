<template>
  <div>
    <v-list-item
      @click="$store.dispatch('doneTask', task.id)"
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

        <v-list-item-action v-if="task.dueDate">
          <v-list-item-action-text>
            <v-icon small>mdi-calendar</v-icon>
            {{  formattedDate(task.dueDate) }}
          </v-list-item-action-text>
        </v-list-item-action>

        <TaskMenu :task='task' />

        <v-list-item-action v-if="$store.state.sorting">
          <v-btn
            color="primary"
            class="handle"
            icon
          >
            <v-icon>mdi-drag-horizontal-variant</v-icon>
          </v-btn>
        </v-list-item-action>
      </template>

    </v-list-item>
    <v-divider></v-divider>

  </div>
</template>

<script>
import { format } from 'date-fns'
import TaskMenu from './TaskMenu.vue'

export default {
  props: ['task'],
  components: { TaskMenu },
  methods: {
    formattedDate(value) {
      return format(new Date(value), 'MMM d')
    }
  }
}
</script>