<template>
  <div class="container pt-5">
    <div class="card">
      <h1
        :style="{
          color: inputValue.length > 5 ? 'darkblue' : 'darkred',
          fontSize: inputValue.length < 6 ? '2rem' : '1.5rem',
        }"
      >
        {{ title }}
      </h1>
      <div class="form-control">
        <input
          type="text"
          :placeholder="placeholderString"
          v-model="inputValue"
          @keypress.enter="addNewNote"
        />
      </div>
      <button class="btn" @click="addNewNote">Add note</button>
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
