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
      countries: [],
      search: "",
    };
  },
  created: function () {
    fetch(`https://restcountries.eu/rest/v2/all`)
      .then((response) => response.json())
      .then((res) => {
        console.log(res);
        this.countries = res;
      });
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