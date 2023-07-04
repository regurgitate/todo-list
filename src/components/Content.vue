<script setup>
import Task from "./Task.vue";
import AddForm from "./AddForm.vue";
</script>

<template>
  <div class="rout-view">
    <div class="row">
      <div class="col s5 offset-s1">
        <Task />
        <Task />
      </div>
      <div class="col s5">
        <AddForm />
      </div>
    </div>
  </div>
</template>

<style scoped>
.rout-view {
  min-height: calc(100vh - 114px);
}
</style>