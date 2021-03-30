<template>
  <div class="home">

    <FieldAddTask/>

    <div v-if="$store.state.tasks.length">
      <ListTasks/>
    </div>

    <div v-else>
      <NoTasks/>
    </div>
    
  </div>
</template>

<script>
import FieldAddTask from '@/components/Todo/FieldAddTask.vue'
import ListTasks from '@/components/Todo/ListTasks.vue'
import NoTasks from '@/components/Todo/NoTasks.vue'

export default {
  name: 'Todo',
  components: { 
    FieldAddTask,
    ListTasks,
    NoTasks
  },
}
</script>


