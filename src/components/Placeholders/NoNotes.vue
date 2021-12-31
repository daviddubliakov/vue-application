<template>
  <div>{{ title }}</div>
</template>

<script>
export default {
  name: "NoNotes",
  data() {
    return {
      title: "You don't have any notes. Create your first note!",
    };
  },
};
</script>

<style scoped>
div {
  display: flex;
  justify-content: center;
}
</style>
