<template>
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
</template>

<script>
export default {
  data() {
    return {
      newTaskTitle: ''
    }
  },
  methods: {
    addTaskHandler() {
      if(!this.newTaskTitle) return
      this.$store.dispatch('addTask', this.newTaskTitle)
      this.newTaskTitle = ''
    }
  }
}
</script>