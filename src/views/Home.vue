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
          @input="updateSearch($event.target.value)"
        />
        <button class="home__btn"></button>
      </div>

      <div class="home__content">
        <h2 class="home__content-title">Страны</h2>
        <div class="home__countries">
          <div
            class="home__country"
            v-for="(country, index) in paginateItems"
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
        <!-- <div class="paginate">
          <a
            href="#top"
            class="paginate__pag"
            v-for="page in pages"
            :class="{ paginate_active: page === pageNumber }"
            :key="page"
            @click.prevent="pageClick(page)"
          >
            {{ page }}
          </a>
        </div> -->

        <paginate
          :page-count="pages"
          :click-handler="pageClick"
          :prev-text="'<'"
          :next-text="'>'"
          :container-class="'paginate'"
        />
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      countries: [],
      itemPage: 30,
      pageNumber: 1,
      search: "",
    };
  },
  created: function () {
    fetch(`https://restcountries.eu/rest/v2/all`)
      .then((response) => response.json())
      .then((res) => {
        console.log(res);
        this.countries = res;
      })
      .then(() => {
        console.log(this.pages);
      });
  },
  computed: {
    pages() {
      return Math.ceil(this.countries.length / this.itemPage);
    },
    paginateItems() {
      let from = (this.pageNumber - 1) * this.itemPage;
      let to = from + this.itemPage;
      return this.countries.slice(from, to);
    },
  },
  methods: {
    searchCountries() {
      let countriesBlock = document.querySelectorAll(".home__country");
      this.countries.forEach((item, index) => {
        if (item.name.toUpperCase().indexOf(this.search.toUpperCase()) > -1) {
          if (countriesBlock[index]) {
            countriesBlock[index].style.display = "";
          }

          this.itemPage = 250;
        } else {
          if (countriesBlock[index]) {
            countriesBlock[index].style.display = "none";
          }
          this.itemPage = 250;
        }
      });

      if (!this.search) {
        this.itemPage = 30;
      }
    },
    updateSearch(value) {
      this.search = value;
      this.searchCountries();
    },
    pageClick(page) {
      this.pageNumber = page;
      window.scroll(0, 0);
    },
  },
};
</script>

<style lang="scss">
</style>
