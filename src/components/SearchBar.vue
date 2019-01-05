<template lang="html">
  <div class="">
    <input type="text" name="" value="" @input="onInput" placeholder="Search Videos">
  </div>
</template>

<script>
export default {
  name: "SearchBar",
  methods: {
    onInput(event) {
      this.$emit('termChange', event.target.value);
    }
  }
}
</script>

<style lang="css" scoped>
  input {
    width: 75%;
  }

  div {
    text-align: center;
    margin: 20px;
  }
</style>
