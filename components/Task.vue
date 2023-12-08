<template lang="pug">
div.tasks-container
  el-row(:gutter="10")
    el-col(:span="20")
      h3(:class="{ 'task-done': task.done }") {{ task.title }}
      p(:class="{ 'task-done': task.done }") {{ task.description }}
    el-col(:span="4")
      el-tag(v-if="task.done" :style="{ color: '#67c23a' }") Done
      el-tag(v-else :style="{ color: '#f56c6c' }") Not done
  el-button.icon-button(@click="toggleDone") {{ task.done ? 'Undone' : 'Done' }}
  el-button.icon-button(@click="editTask") Edit
</template>

<script>
export default {
  props: {
    task: {
      type: Object,
      required: true
    }
  },
  methods: {
    toggleDone() {
      this.$emit('toggleTaskDone');
    },
    editTask() {
    }
  }
};
</script>

<style>
.icon-button {
  margin-left: 5px;
}

.task-done {
  text-decoration: line-through;
  opacity: 0.5;
}
</style>
