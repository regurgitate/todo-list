<script setup>
import Task from "./Task.vue";
import AddForm from "./AddForm.vue";
 
const props = defineProps(['data', 'statuses']);
</script>

<template>
  <div class="rout-view">
    <div class="row">
      <div class="col s5 offset-s1">
        <Task v-for="datum in data" :key="datum.id" :task="datum" :statusInfo="statuses.filter(status => status.name === datum.status)[0]" />
      </div>
      <div class="col s5">
        <AddForm :statuses="statuses" />
      </div>
    </div>
  </div>
</template>

<style scoped>
.rout-view {
  min-height: calc(100vh - 114px);
}
</style>