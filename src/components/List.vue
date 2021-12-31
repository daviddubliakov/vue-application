<template>
  <ul class="list">
    <li class="list-item" v-for="(item, index) in data" :key="index">
      {{ index + 1 }}. {{ toUpperCase(item) }}
      <button class="btn danger" @click="deleteElement(index)">Delete</button>
    </li>
    <hr />
    <li>
      <strong>Overall quantity: {{ data.length }}</strong>
    </li>
  </ul>
</template>

<script>
export default {
  name: "List",
  props: {
    data: Array,
  },
  methods: {
    deleteElement(elementIndex) {
      this.$props.data.splice(elementIndex, 1);
    },
    toUpperCase(text) {
      return text.toUpperCase();
    },
  },
};
</script>
