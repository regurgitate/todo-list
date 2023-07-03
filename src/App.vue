<script setup>
import Navi from "./components/Navi.vue";
import Content from "./components/Navi.vue";
import Foot from "./components/Navi.vue";

import 'materialize-css/dist/css/materialize.min.css';
import 'materialize-css/dist/js/materialize.min.js';
</script>

<script>
export default {
  data() {
    return {
      toDoList: [
        "Laundry",
        "Shopping",
        "Take out the garbage",
        "Interview exercise",
        "Squaring the circle",
        "Doubling the cube",
        "Angle trisection"
      ]
    }
  }
}
</script>


<template>
  <Navi />
  <Content />
  <Foot />
</template>

<style scoped>

</style>
