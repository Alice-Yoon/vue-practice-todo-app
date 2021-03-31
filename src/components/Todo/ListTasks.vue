<template>
  <v-list
    class="pt-0"
    flat
  >
    <Task 
      v-for="task in $store.getters.tasksFiltered"
      :key="task.id"
      :task='task'
    />
  </v-list>
</template>

<script>
import Task from '@/components/Todo/Task.vue'

export default {
  components: {
    Task
  }
}
</script>