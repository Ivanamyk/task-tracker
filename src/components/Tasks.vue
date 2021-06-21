<template>
  <div>
    <div v-bind:key="task.id" v-for="task in tasks">
      <!--as the data i want to call is one level higher, i create another emit so i can reach it -->
      <Task
        v-on:toggle-reminder="$emit('toggle-reminder', task.id)"
        v-on:delete-task="$emit('delete-task', task.id)"
        :task="task"
      />
    </div>
  </div>
</template>

<script>
import Task from "./Task.vue";
export default {
  name: "Tasks",
  props: {
    tasks: Array,
  },
  components: {
    Task,
  },
  //i add this to tag my emits and prevent my console to send error message about it.
  emits: ["delete-task", "toggle-reminder"],
};
</script>