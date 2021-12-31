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
      <hr />
      <strong>Doubled: {{ doubleNotesComputed }} </strong>
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
      notes: [],
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
  computed: {
    doubleNotesComputed() {
      return this.notes.length * 2;
    },
  },
  watch: {
    inputValue(value) {
      if (value.length > 10) {
        this.inputValue = "";
      }
    },
  },
};
</script>
