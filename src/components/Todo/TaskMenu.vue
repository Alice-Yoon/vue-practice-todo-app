<template>
<div>
  <v-menu
    bottom
    left
  >
    <template v-slot:activator="{ on, attrs }">
      <v-btn
        icon
        v-bind="attrs"
        v-on="on"
      >
        <v-icon>mdi-dots-vertical</v-icon>
      </v-btn>
    </template>

    <v-list>
      <v-list-item
        v-for="(item, index) in items"
        :key="index"
        @click="handleClick(index)"
      >
        <v-list-item-icon>
          <v-icon v-text="item.icon"></v-icon>
        </v-list-item-icon>
        <v-list-item-title>{{ item.title }}</v-list-item-title>
      </v-list-item>
    </v-list>
  </v-menu>

  <DialogDelete v-if="dialogs.delete" @close='dialogs.delete = false' :task='task' />
</div>
</template>

<script>
import DialogDelete from './Dialogs/DialogDelete.vue'

export default {
  props: ['task'],
  components: { DialogDelete },
  data() {
    return {
      dialogs: {
        delete: false
      },
      items: [
        { 
          title: 'Edit',
          icon: 'mdi-pencil',
          click() {

          } 
        },
        { 
          title: 'Due date',
          icon: 'mdi-calendar',
          click() {

          } 
        },
        { 
          title: 'Delete',
          icon: 'mdi-delete',
          click() {
            this.dialogs.delete = true
          } 
        },
      ]
    }
  },
  methods: {
    handleClick(index) {
      this.items[index].click.call(this)
    }
  }
}
</script>

<style>

</style>