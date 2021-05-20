<template>
  <section class="result">
    <div class="container">
      <div class="result__back" @click="$router.push('/')">
        <img src="@/assets/images/icons/arrow.svg" alt="back" />
        <p>Назад</p>
      </div>
      <div class="home__content">
        <div class="home__countries">
          <div
            class="home__country"
            v-for="(country, index) in countries"
            :key="index"
          >
            <img class="home__country-flag" :src="country.flag" alt="flag" />
            <h3 class="home__country-name">
              {{ country.name }}
            </h3>
            <p class="home__country-alpha-code">
              Код сраны: <span>{{ country.alpha3Code }}</span>
            </p>
            <p class="home__country-alpha-code">
              Код сраны короткий: <span>{{ country.alpha2Code }}</span>
            </p>
            <p class="home__country-alpha-code">
              Телефонный код: <span>+{{ country.callingCodes[0] }}</span>
            </p>
            <p class="home__country-alpha-code">
              Столица: <span>{{ country.capital }}</span>
            </p>
            <p class="home__country-alpha-code">
              Население: <span>{{ country.population }}</span>
            </p>
            <p class="home__country-alpha-code">
              Валюта:
              <span
                ><p v-if="country.currencies[0].symbol">
                  {{ country.currencies[0].symbol }}
                </p>
                {{ country.currencies[0].code }}</span
              >
            </p>
            <p class="home__country-alpha-code">
              Языки:
              <span
                ><p v-for="(language, index) in country.languages" :key="index">
                  {{ language.name }},
                </p></span
              >
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
      query: this.$route.query.country,
      countries: [],
      search: "",
    };
  },
  created: function () {
    fetch(`https://restcountries.eu/rest/v2/name/${this.query}`)
      .then((response) => response.json())
      .then((res) => {
        console.log(res);
        this.countries = res;
      });
  },
};
</script>

<style lang="scss">
</style>