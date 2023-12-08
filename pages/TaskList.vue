<template lang="pug">
el-container(:style="{ height: '100vh' }")
  el-main
    el-row
      el-col
        h1 Ma liste de tâches
        el-row
          el-col
            div.tasks-list
              Task(v-for="(task, index) in tasks" :key="index" :task="task" @toggleTaskDone="toggleTaskDone(index)")
</template>

<script>
import Task from '~/components/Task.vue';

export default {
  components: {
    Task
  },
  data() {
    return {
      tasks: [
        { id:1, title: 'Faire les courses', description: 'Acheter des légumes et du lait', done: false },
        { id:2, title: 'Ceci est une tâche', description: 'Ceci est une description', done: false },
      ]
    };
  },
  methods: {
    toggleTaskDone(index) {
      this.$set(this.tasks[index], 'done', !this.tasks[index].done);
    }
  }
};
</script>
  