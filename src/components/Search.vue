<template>
  <section>
    <input
      class="input-style px-2"
      type="text"
      v-model="inputText"
      placeholder="Film, serie tv..."
      @keyup.enter="$emit('inputSearch', inputText)"
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