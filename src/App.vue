<template>
  <v-app>
    <v-container>
      <ToDo :title="title"></ToDo>
    </v-container>
  </v-app>
</template>

<script>
import ToDo from "./components/ToDo";
export default {
  name: "App",
  data: () => ({
    title: "To Do List"
  }),
  components: {
    ToDo
  }
};
</script>
