<template>
  <section>
    <input type="text" v-model="inputText" />
    <button @click="$emit('inputSearch', inputText)">Cerca</button>
  </section>
</template>

<script>
export default {
  name: "Search",
  data() {
    return {
      inputText: "",
    };
  },
  methods: {},
};
</script>

<style>
</style>