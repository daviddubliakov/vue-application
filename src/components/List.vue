<template>
  <ul class="list">
    <li class="list-item" v-for="(item, index) in data" :key="index">
      {{ item }}
      <button class="btn danger" @click="deleteElement(index)">Delete</button>
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
  },
};
</script>
