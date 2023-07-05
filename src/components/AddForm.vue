<script setup>
const props = defineProps(['statuses']);
</script>

<script>
export default {
  data() {
    return {
      task: {
        title: '',
        content: '',
        status: 'New'
      },
      errorMsg: ""
    }
  },
  mounted() {
    M.FormSelect.init(this.$refs.select);
  },
  methods: {
    submit: function() {
      if (!this.task.title || !this.task.content) {
        this.errorMsg = "Fill up the form"
      } else {
        this.errorMsg = "";
        const data = { ...this.task };
        this.$emit("addNewTask", data);
        this.task.title = "";
        this.task.content = "";
        this.task.status = "New";
        this.$refs.form.reset();
      }
    }
  }
}
</script>

<template>
  <div class="row">
    <div class="form-container col s12">
      <h5 class="title">Add new task</h5>
      <form ref="form" @submit.prevent="submit">
        <div class="input-field">
          <input id="title" type="text" class="validate" v-model="task.title">
          <label for="title">Title</label>
        </div>
        <div class="input-field">
          <textarea id="content" class="materialize-textarea" v-model="task.content"></textarea>
          <label for="content">Content</label>
        </div>
        <div class="input-field">
          <select ref="select" v-model="task.status">
            <option v-for="status in statuses" :key="status.name">{{ status.name }}</option>
          </select>
          <label>Select status</label>
        </div>
        <div class="container">
          <div class="row center-align">
            <p class="error">{{ errorMsg }}</p>
            <button class="btn waves-effect waves-light center">
              Submit
              <i class="material-icons right">send</i>
            </button>
          </div>
        </div>
      </form>
    </div>
  </div>
</template>

<style scoped>
.error {
  color: crimson;
  font-weight: bold;
}
.title {
  margin-bottom: 30px;
}
.form-container {
  border: 2px solid grey;
  border-radius: 5px;
  margin-top: 7.5px;
}
</style>