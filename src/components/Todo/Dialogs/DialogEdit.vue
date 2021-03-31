<template>
  <v-dialog
    :value='true'
    persistent
    max-width="290"
  >
    <v-card>
      <v-card-title class="headline">
        Edit Task?
      </v-card-title>
      <v-card-text>
       Edit the title of this task:
      </v-card-text>

      <v-text-field 
        v-model="taskTitle" 
        @keyup.enter="saveTask"
      />

      <v-card-actions>
        <v-spacer></v-spacer>
        <v-btn
          @click="$emit('close')"
          text
        >
          Cancel
        </v-btn>
        <v-btn
          @click="saveTask"
          color="red darken-1"
          text
        >
          Save
        </v-btn>
      </v-card-actions>
    </v-card>
  </v-dialog>
</template>

<script setup>
  export default {
    props: ['task'],
    data() {
      return {
        taskTitle: null
      }
    },
    mounted() {
      this.taskTitle = this.task.title
    },
    methods: {
      saveTask() {
        const payload = {
          id: this.task.id,
          title: this.taskTitle
        }
        this.$store.dispatch('updateTask', payload)
        this.$emit('close')
      }
    }
  }
</script>
