<script setup>
const props = defineProps(['task', 'statusInfo']);
</script>

<script>
export default {
  data() {
    return {

    }
  },
  methods: {

  }
};
</script>

<template>
  <div class="card" :class="statusInfo.color">
    <div class="card-content white-text">
      <span class="card-title" :style="statusInfo.text || ''">{{ task.title }}</span>
      <p :style="statusInfo.text || ''">{{ task.content }}</p>
    </div>
    <div class="card-action white-text">
      <i class="material-icons icon-left">{{ statusInfo.icon }}</i>
      <span>{{ task.status }}</span>
      <span class="right">
        <i class="material-icons icon-right">create</i>
        <i class="material-icons icon-right" @click="$emit('deleteTask', task.id)">delete_sweep</i>
      </span>
    </div>
  </div>
</template>

<style scoped>
.icon-left {
  position: relative;
  margin: 0 8px 0 0;
  top: 6px;
}
.icon-right {
  position: relative;
  margin: 0 8px;
  top: 6px;
  cursor: pointer;
}
</style>