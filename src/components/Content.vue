<script setup>
import Task from "./Task.vue";
import AddForm from "./AddForm.vue";
 
const props = defineProps(['data', 'statuses']);
</script>

<template>
  <div class="rout-view">
    <div class="row">
      <div class="col s5 offset-s1">
        <Task
          v-for="datum in data"
          :key="datum.id"
          :task="datum"
          :statusInfo="statuses.filter(status => status.name === datum.status)[0]"
          @deleteTask="$emit('deleteTask', $event)"
        />
        <h5 class="all-done" v-if="data.length === 0">
          It looks like you've done eveything :) Time to play
        </h5>
      </div>
      <div class="col s5">
        <AddForm :statuses="statuses" @addNewTask="$emit('addNewTask', $event)" />
      </div>
    </div>
  </div>
</template>

<style scoped>
.all-done {
  margin-top: 40px;
}
.rout-view {
  min-height: calc(100vh - 114px);
}
</style>