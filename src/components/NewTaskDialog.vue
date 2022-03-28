<template>
  <v-dialog
    max-width="400"
    v-model="showDialog"
  >
      <!-- Pass on all named slots -->
      <slot 
        v-for="slot in Object.keys($slots)"
        :name="slot"
        :slot="slot"
      />
    
      <!-- Pass on all scoped slots -->
      <template
        v-for="slot in Object.keys($scopedSlots)"
        :slot="slot"
        slot-scope="scope"
      >
        <slot :name="slot" v-bind="scope"/>
      </template>
      <v-card>
        <v-card-title>Create your new task:</v-card-title>
        <v-card-text>
          <v-text-field
            label="Title"
            v-model="title"
          ></v-text-field>
          <v-text-field
            label="Description"
            v-model="description"
          ></v-text-field>
        </v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            text
            @click="cancel"
          >Cancel</v-btn>
          <v-btn
            color="primary"
            @click="sendTask"
          >Save</v-btn>
        </v-card-actions>
      </v-card> 
  </v-dialog>
</template>

<script>
export default {
  name: 'NewTaskDialog',
  props: {
    // task: { type: Object }
  },
  data() {
    return {
      showDialog: false,
      title: '',
      description: '',
    }
  },
  methods: {
    cancel() {
      this.showDialog = false;
    },
    sendTask() {
      this.$emit('setNewTask', {
        id: Date.now(),
        title: this.title,
        description: this.description,
      });
      this.showDialog = false;
      this.title = '';
      this.description = '';
    }
  }
}
</script>

<style>

</style>