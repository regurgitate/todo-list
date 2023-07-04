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
        status: ''
      }
    }
  },
  mounted() {
    M.FormSelect.init(this.$refs.select);
  },
  methods: {
    submit: function() {
      this.$refs.form.reset();
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
          <input id="title" type="text" class="validate">
          <label for="title">Title</label>
        </div>
        <div class="input-field">
          <textarea id="content" class="materialize-textarea"></textarea>
          <label for="content">Content</label>
        </div>
        <div class="input-field">
          <select ref="select">
            <option v-for="status in statuses" :key="status.name" value="status.name">{{ status.name }}</option>
          </select>
          <label>Select status</label>
        </div>
        <div class="container">
          <div class="row center-align">
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
.title {
  margin-bottom: 30px;
}
.form-container {
  border: 2px solid grey;
  border-radius: 5px;
  margin-top: 7.5px;
}
</style>