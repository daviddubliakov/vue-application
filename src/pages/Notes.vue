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

<style scoped>
.form-control {
  position: relative;
  margin-bottom: 0.5rem;
}

.form-control input,
.form-control select {
  margin: 0;
  outline: none;
  border: 2px solid #ccc;
  display: block;
  width: 100%;
  color: #2c3e50;
  padding: 0.5rem 1.5rem;
  border-radius: 3px;
  font-size: 1rem;
}

.form-control small {
  color: #e53935;
}

.form-control.invalid input {
  border-color: #e53935;
}

.form-checkbox {
  margin-bottom: 1rem;
}

.form-checkbox .label {
  display: block;
  margin: 0 0 0.3rem 0.3rem;
  font-weight: 500;
}

.form-checkbox .checkbox input {
  margin-right: 1rem;
}

.form-control label {
  display: block;
  margin: 0 0 0.3rem 0.3rem;
  font-weight: 500;
}

.form-control input:active,
.form-control input:focus {
  transition: border 0.22s;
  border: 2px solid #42b983;
}

.card {
  overflow: hidden;
  padding: 1rem;
  margin-bottom: 1rem;
  border-radius: 10px;
  box-shadow: 2px 3px 10px rgba(0, 0, 0, 0.2);
  background: #fff;
}

.card.marked {
  border: 4px solid #42b983;
}

.card.center {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
