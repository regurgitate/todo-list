<script setup>
const props = defineProps(['task', 'statusInfo', 'statusesNames']);
</script>

<script>
export default {
  data() {
    return {
      editMode: false,
      editIcon: 'create',
      editColor: "",
    }
  },
  methods: {
    edit() {
      if (!this.editMode) {
        this.editMode = true;
        this.editIcon = "save";
      } else {
        this.editMode = false;
        this.editIcon = "create";
        this.$emit("updateTask", {
          title: this.$refs.title.innerHTML,
          content: this.$refs.content.innerHTML,
          status: this.$refs.select.value,
          id: this.task.id
        });
      }
    }
  },
  mounted() {
    M.FormSelect.init(this.$refs.select);
  }
};
</script>

<template>
  <div class="card" :class="editMode ? 'grey lighten-1 editable' : statusInfo.color">
    <div class="card-content" :class="editMode ? 'black-text' : 'white-text'">
      <span 
        class="card-title"
        :class="editMode ? 'editable' : ''"
        :contenteditable="editMode"
        :style="statusInfo.text || ''"
        ref="title"
      >
        {{ task.title }}
      </span>
      <p
        :class="editMode ? 'editable' : ''"
        :style="statusInfo.text || ''"
        :contenteditable="editMode"
        ref="content"
      >
        {{ task.content }}
      </p>
    </div>
    <div class="card-action" :class="editMode ? 'black-text' : 'white-text'">
      <i class="material-icons icon-left">{{ statusInfo.icon }}</i>
      <span v-if="!editMode">{{ task.status }}</span>

      <div v-show="editMode" class="input-field inline">
        <select ref="select">
          <option 
            v-for="status in statusesNames"
            :key="status"
            :selected="status === task.status"
          >
            {{ status }}
          </option>
        </select>
      </div>

      <span class="right">
        <i class="material-icons icon-right" @click="edit">{{ editIcon }}</i>
        <i class="material-icons icon-right" @click="$emit('deleteTask', task.id)">delete_sweep</i>
      </span>
    </div>
  </div>
</template>

<style scoped>
.editable {
  border: 2px solid grey;
  border-radius: 5px;
}
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