<template>
  <v-list-item>
    <v-list-item-action>
      <v-checkbox v-model="toDoData.is_complete"></v-checkbox>
    </v-list-item-action>
    <v-list-item-content>
      <v-list-item-title>
        <span :class="{'is-complete':toDoData.is_complete}">{{toDoData.name}}</span>
      </v-list-item-title>
    </v-list-item-content>
    <v-list-item-action>
      <v-btn icon @click="$emit('removeItem',toDoData.id)">
        <v-icon color="red lighten-1">mdi-close-circle</v-icon>
      </v-btn>
    </v-list-item-action>
  </v-list-item>
</template>

<script>
export default {
  props: ["toDoData"]
};
</script>

<style scoped>
.is-complete {
  text-decoration: line-through;
}
</style>
