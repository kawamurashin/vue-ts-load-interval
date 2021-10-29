<template>
  <div>
    <div>Child</div>
    <div>{{ name }}</div>
    <div>{{ message }}</div>
  </div><br>
</template>

<script lang="ts">
export default {
  name: "Child",
  props: [
    "name",'message'],
}
</script>

<style scoped>
</style>