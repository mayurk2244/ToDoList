<template>
  <v-card class="mx-auto mt-10" width="400">
    <v-card-title>
      <span>
        <v-icon color="pink">mdi-square-edit-outline</v-icon>
        {{title}}
      </span>
    </v-card-title>
    <v-divider></v-divider>
    <v-card-text>
      <ToDoField v-on:addItem="addItem" />
      <div class="task-list" v-if="toDoListData.length">
        <div v-for="toDoList in toDoListData" :key="toDoList.id">
          <ToDoItem :toDoData="toDoList" v-on:removeItem="removeItem" />
          <v-divider></v-divider>
        </div>
      </div>
      <h4 v-else class="text-center">Todo list is empty</h4>
    </v-card-text>
  </v-card>
</template>
<script>
import ToDoField from "./ToDoField";
import ToDoItem from "./ToDoItem";
export default {
  props: ["title"],
  data: function() {
    return {
      toDoListData: []
    };
  },
  components: {
    ToDoField,
    ToDoItem
  },
  methods: {
    removeItem(toDoId) {
      this.toDoListData = this.toDoListData.filter(data => data.id != toDoId);
    },
    addItem(newItemData) {
      this.toDoListData = [...this.toDoListData, newItemData];
    }
  }
};
</script>
<style scoped>
.task-list {
  max-height: 200px;
  overflow-y: auto;
}
</style>