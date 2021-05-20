<template>
  <section class="home">
    <div class="container">
      <div class="home__header">
        <h1 class="home__title">Справочник со странами</h1>
      </div>

      <div class="home__search">
        <input
          type="text"
          class="home__inp"
          placeholder="Поиск стран"
          @input="searchCountries"
          v-model="search"
        />
        <button class="home__btn"></button>
      </div>

      <div class="home__content">
        <h2 class="home__content-title">Страны</h2>
        <div class="home__countries">
          <div
            class="home__country"
            v-for="(country, index) in countries"
            :key="index"
            @click="
              $router.push({
                path: '/search-result',
                query: { country: country.name },
              })
            "
          >
            <img class="home__country-flag" :src="country.flag" alt="flag" />
            <h3 class="home__country-name">
              {{ index + 1 }} - {{ country.name }}
            </h3>
            <p class="home__country-alpha-code">
              Код сраны: <span>{{ country.alpha2Code }}</span>
            </p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
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
  },
  methods: {
    searchCountries() {
      let countriesBlock = document.querySelectorAll(".home__country");
      this.countries.forEach((item, index) => {
        if (item.name.toUpperCase().indexOf(this.search.toUpperCase()) > -1) {
          countriesBlock[index].style.display = "";
        } else {
          countriesBlock[index].style.display = "none";
        }
      });
    },
  },
};
</script>

<style lang="scss">
</style>
