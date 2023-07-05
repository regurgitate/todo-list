<script setup>
import Navi from "./components/Navi.vue";
import Content from "./components/Content.vue";
import Foot from "./components/Foot.vue";

import 'materialize-css/dist/css/materialize.min.css';
import 'materialize-css/dist/js/materialize.min.js';
</script>

<script>
export default {
  data() {
    return {
      toDoList: [
        {
          title: "Laundry",
          content: "three loads of laundry to do - colored, white, and delicate",
          status: "New",
          id: 1
        },
        {
          title: "Shopping",
          content: "bred, milk, a car, fruits, butter",
          status: "Completed",
          id: 2
        },
        {
          title: "Take out the garbage",
          content: "Now I have to wait because the communal trash bin is under renovation",
          status: "On Hold",
          id: 3
        },
        {
          title: "Interview exercise",
          content: "I have 4 days more to complete all tasks",
          status: "In Progress",
          id: 4
        },
        {
          title: "Squaring the circle",
          content: "This is too tricky for me to complete",
          status: "Abandoned",
          id: 5
        },
        {
          title: "Doubling the cube",
          content: "Man I tell you I thought I'm better at math",
          status: "Abandoned",
          id: 6
        },
        {
          title: "Angle trisection",
          content: "Homework for next week",
          status: "In Progress",
          id: 7
        }
      ],
      statuses: [
        {
          name: "New",
          color: "cyan",
          icon: "fiber_new"
        },
        {
          name: "In Progress",
          color: "orange",
          icon: "build"
        },
        {
          name: "Completed",
          color: "green darken-1",
          icon: "done",
          text: "text-decoration: line-through"
        },
        {
          name: "On Hold",
          color: "deep-purple",
          icon: "block"
        },
        {
          name: "Abandoned",
          color: "brown lighten-1",
          icon: "highlight_off",
          text: "text-decoration: line-through"
        },
      ]
    }
  },
  methods: {
    deleteTask(id) {
      const index = this.toDoList.findIndex(item => item.id === id);

      if (index !== -1) {
        this.toDoList.splice(index, 1);
      }
    },
    addNewTask(task) {
      let maxID = Math.max(...this.toDoList.map(o => o.id));
      task.id = maxID === -Infinity ? 1 : ++maxID;
      this.toDoList.unshift(task);
    }
  }
}
</script>


<template>
  <Navi />
  <Content
    :data="toDoList"
    :statuses="statuses"
    @deleteTask="deleteTask($event)"
    @addNewTask="addNewTask($event)"
  />
  <Foot />
</template>

<style>

</style>
