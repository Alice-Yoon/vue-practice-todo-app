<template>
  <div class="home">

    <FieldAddTask/>

    <div v-if="$store.state.tasks.length">
      <ListTasks/>
    </div>

    <div v-else>
      <NoTasks/>
    </div>

    <ButtonDoneSorting v-if="$store.state.sorting" />
    
  </div>
</template>

<script>
import FieldAddTask from '@/components/Todo/FieldAddTask.vue'
import ListTasks from '@/components/Todo/ListTasks.vue'
import NoTasks from '@/components/Todo/NoTasks.vue'
import ButtonDoneSorting from '@/components/Todo/ButtonDoneSorting.vue'

export default {
  name: 'Todo',
  components: { 
    FieldAddTask,
    ListTasks,
    NoTasks,
    ButtonDoneSorting
  },
}
</script>


