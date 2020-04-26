<template>
  <v-form ref="TaskForm" @submit.prevent="addNewItem()">
    <v-row>
      <v-col cols="10">
        <v-text-field label="Todo" v-model="task_name" outlined></v-text-field>
      </v-col>
      <v-col cols="2">
        <v-btn fab dark small color="pink" type="submit">
          <v-icon dark>mdi-content-save</v-icon>
        </v-btn>
      </v-col>
    </v-row>
  </v-form>
</template>

<script>
import { v4 as uuidv4 } from "uuid";
export default {
  data: () => ({
    task_name: null
  }),
  methods: {
    addNewItem() {
      if (this.task_name) {
        let task_data = {
          id: uuidv4(),
          name: this.task_name,
          is_complete: false
        };
        this.$emit("addItem", task_data);
        this.$refs.TaskForm.reset();
      }
    }
  }
};
</script>

<style>
</style>