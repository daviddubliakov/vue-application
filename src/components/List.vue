<template>
  <ul class="list">
    <li class="list-item" v-for="(item, index) in data" :key="index">
      <!-- <span :class="{ bold: item.length < 5 }">
        {{ index + 1 }}. {{ toUpperCase(item) }}
      </span> -->
      <span :class="['bold', { primary: item.length > 5 }]">
        {{ index + 1 }}. {{ toUpperCase(item) }}
      </span>
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

<style scoped>
.list {
  margin: 0;
  padding: 0;
  list-style: none;
}

.list-item {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0.5rem 0;
  transition: 0.22s all;
  text-overflow: ellipsis;
  white-space: nowrap;
  overflow: hidden;
}

.list-item:hover {
  background: #eee;
}
</style>
