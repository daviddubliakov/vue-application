<template>
  <div class="container pt-5">
    <div class="card">
      <h1>{{ title }}</h1>
      <div class="form-control">
        <input
          type="text"
          :placeholder="placeholderString"
          :value="inputValue"
          @input="inputChangeHandler"
          @keypress.enter="addNewNote"
        />
      </div>
      <button class="btn" v-on:click="addNewNote">Add note</button>
      <hr />
      <List :data="notes" v-if="notes.length !== 0" />
      <NoNotes v-else />
    </div>
  </div>
</template>

<script>
import List from "../components/List.vue";
import NoNotes from "../components/Placeholders/NoNotes.vue";

export default {
  name: "Notes",
  components: {
    List,
    NoNotes,
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
      if (this.inputValue !== "") {
        this.notes.push(this.inputValue);
        this.inputValue = "";
      }
    },
  },
};
</script>
