<template>
  <section>
    <input
      class="input-style"
      type="text"
      v-model="inputText"
      placeholder=" Film, serie tv..."
    />
    <button class="px-3" @click="$emit('inputSearch', inputText)">Cerca</button>
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
.input-style {
  color: gray;
  font-family: sans-serif;
}

button {
  background-color: #e50914;
  color: white;
}
</style>