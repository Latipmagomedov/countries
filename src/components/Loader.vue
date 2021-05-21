<template>
  <div class="preloader" v-if="loader">
    <div class="loader">loading</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      loader: true,
    };
  },
  created: function () {
    window.onload = () => {
      this.loader = false;
    };
  },
  watch: {
    $route() {
      this.loader = true;

      setTimeout(() => {
        this.loader = false;
      }, 300);
    },
  },
};
</script>

<style>
</style>