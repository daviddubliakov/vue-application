<template>
  <div class="container pt-5">
    <div class="card">
      <h1>{{ title }}</h1>
      <div class="form-control">
        <input
          type="text"
          :placeholder="placeholderString"
          :value="inputValue"
          v-on:input="inputChangeHandler"
          v-on:keypress.enter="addNewNote"
        />
      </div>
      <button class="btn" v-on:click="addNewNote">Add note</button>
      <hr />
      <List :data="notes" />
    </div>
  </div>
</template>

<script>
import List from "../components/List.vue";

export default {
  name: "Notes",
  components: {
    List,
  },
  data() {
    return {
      title: "Notes",
      inputValue: "",
      placeholderString: "Write a note title...",
      notes: ["Note 1", "Note 2"],
    };
  },
  methods: {
    inputChangeHandler(event) {
      this.inputValue = event.target.value;
    },
    addNewNote() {
      this.notes.push(this.inputValue);
      this.inputValue = "";
    },
  },
};
</script>
