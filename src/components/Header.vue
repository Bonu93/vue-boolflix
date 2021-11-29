<template>
  <header>
      <input type="text"
      v-model="userQuery"
      @keyup.enter="$emit('search', userQuery)"
      >

      <button
      @click="$emit('search', userQuery)"
      >
          Search
      </button>
  </header>
</template>

<script>
export default {
    name: 'Header',
    data() {
        return {
            userQuery: "",
        }
    },
}
</script>

<style lang="scss" scoped>

</style>