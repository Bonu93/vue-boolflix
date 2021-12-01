<template>
  <header class="p-3">
      <div class="container d-flex justify-content-between align-items-center">
          <div class="brand">
              <img src="https://fontmeme.com/permalink/211201/23ce322a0021620e5e3988113b05d104.png" alt="">
          </div>
          <div class="cta d-flex align-items-center">
            <input type="text"
            class="bg-dark"
            v-model.trim="userQuery"
            @keyup.enter="$emit('search', userQuery)"
            >

            <button
            class="btn btn-dark"
            @click="$emit('search', userQuery)"
            >
                Search
            </button>
          </div>

      </div>
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
    .brand {
        img{
            width: 300px;
        }
    }

    .cta {
        color: white;
        input {
            outline: none;
            color: white;
        }
    }
</style>