<template>
  <div id="app">
    <Loader />
    <router-view />
  </div>
</template>

<script>
import Loader from "@/components/Loader.vue";
export default {
  components: {
    Loader,
  },
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Montserrat:wght@100;200;300;400;500;600;700;800;900&display=swap");

$blue: #1771f1;

// Light
$light-bg: #fff;
$light-col: #000000;
$light-elem-bg: #e6e7e8;
$light-elem-col: #111111;

// Dark
$dark-bg: #0e0e0e;
$dark-col: #e9e9e9;
$dark-elem-bg: #1b1b1b;
$dark-elem-col: #eeeeee;

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  outline: none;
}

body {
  background-color: $light-bg;
  color: $light-col;
  font-family: "Montserrat", sans-serif;
}

.preloader {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  min-height: 600px;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: $dark-bg;
  z-index: 99;
}

.loader,
.loader:after {
  overflow: hidden;
  border-radius: 50%;
  width: 70px;
  height: 70px;
}
.loader {
  margin: 0px auto;
  margin-top: -50px;
  font-size: 10px;
  position: relative;
  text-indent: -9999em;
  border-top: 10px solid rgba(101, 171, 248, 0.2);
  border-right: 10px solid rgba(101, 171, 248, 0.2);
  border-bottom: 10px solid rgba(101, 171, 248, 0.2);
  border-left: 10px solid #65abf8;
  -webkit-transform: translateZ(0);
  -ms-transform: translateZ(0);
  transform: translateZ(0);
  -webkit-animation: load8 1.1s infinite linear;
  animation: load8 1.1s infinite linear;
}
@-webkit-keyframes load8 {
  0% {
    -webkit-transform: rotate(0deg);
    transform: rotate(0deg);
  }
  100% {
    -webkit-transform: rotate(360deg);
    transform: rotate(360deg);
  }
}
@keyframes load8 {
  0% {
    -webkit-transform: rotate(0deg);
    transform: rotate(0deg);
  }
  100% {
    -webkit-transform: rotate(360deg);
    transform: rotate(360deg);
  }
}

.container {
  width: 93%;
  max-width: 480px;
  margin: 0 auto;
}

a {
  color: $blue;
  text-decoration: none;
}

button,
input {
  background-color: $light-elem-bg;
  color: $light-elem-col;
  height: 50px;
  border-radius: 13px;
  border: none;
  box-shadow: none;
  font-family: "Montserrat", sans-serif;
  font-size: 15px;
  font-weight: 600;
}

button {
  padding: 0 13px;
}

input {
  padding-left: 15px;
}

.home__title {
  max-width: 230px;
  margin-top: 40px;
  font-size: 30px;
  font-weight: 800;
  line-height: 1.1;
}

.home__search {
  margin-top: 15px;
  width: 100%;
  height: 50px;
  border-radius: 13px;
  background-color: $light-elem-bg;
  display: flex;
  align-items: center;
  justify-content: space-between;

  .home__inp {
    background-color: transparent;
    width: 100%;
  }

  .home__btn {
    min-width: 50px;
    max-width: 50px;
    background-color: transparent;
    background-image: url(assets/images/icons/search.svg);
    background-size: 40%;
    background-position: center;
    background-repeat: no-repeat;
  }
}

.home__content {
  margin-top: 33px;

  .home__content-title {
    font-size: 25px;
    font-weight: 700;
  }

  .home__countries {
    margin-top: 20px;
    padding-bottom: 20px;
  }

  .home__country {
    width: 100%;
    padding: 20px 15px;
    border-radius: 13px;
    background-color: $light-elem-bg;
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;

    &:not(:first-child) {
      margin-top: 20px;
    }

    .home__country-flag {
      max-width: 100%;
      border-radius: 8px;
    }

    .home__country-name {
      max-width: 290px;
      margin-top: 15px;
      padding: 5px 15px;
      border-radius: 10px;
      background-color: $blue;
      color: #fff;
      font-size: 20px;
    }

    .home__country-alpha-code {
      max-width: 280px;
      margin-top: 8px;
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      font-size: 18px;
      font-weight: 600;
      span {
        margin-left: 10px;
        margin-bottom: 8px;
        padding: 4px 10px;
        border-radius: 7px;
        background-color: #fc1a1a;
        color: #fff;
      }
    }
  }
}

.result {
  position: relative;
  display: flex;
  align-items: center;

  .container {
    position: relative;
    display: flex;
    flex-direction: column;
  }

  .home__countries {
    margin-top: 0;
  }

  .result__back {
    margin-top: 20px;
    display: flex;
    align-items: center;
    cursor: pointer;

    p {
      margin-left: 10px;
      color: $blue;
      font-size: 14px;
      font-weight: 600;
    }
  }

  // .home__content {
  //   min-height: 600px;
  //   margin-top: 0px;
  //   // padding-top: 150px;

  //   .home__countries {
  //     margin-top: 200px;
  //   }
  // }
}

.paginate {
  margin-top: 40px;
  padding-bottom: 25px;
  display: flex;
  justify-content: center;
  align-items: center;

  .paginate__pag {
    padding: 10px 15px;
    background-color: $blue;
    color: #fff;
    list-style: none;
    cursor: pointer;

    &:hover {
      background-color: #000;
    }
    a {
      color: #fff;
    }
  }

  .paginate_active {
    background-color: #000;
    color: #fff;
  }
}

.paginate {
  margin-top: 40px;
  padding-bottom: 25px;
  display: flex;
  justify-content: center;
  align-items: center;

  li {
    list-style: none;


    a {
      padding: 10px 15px;
      background-color: $blue;
      color: #fff;
      list-style: none;
      cursor: pointer;
      color: #fff;
      &:hover {
        background-color: #000;
      }
    }
  }

  .active {
    a {
      background-color: #000;
      color: #fff;
    }
  }
}

body.dark {
  background-color: $dark-bg;
  color: $dark-col;
  button,
  input {
    color: $dark-elem-col;
  }

  .home__search {
    background-color: $dark-elem-bg;

    .home__btn {
      background-image: url(assets/images/icons/search-dark.svg);
    }
  }

  .home__content {
    .home__country {
      background-color: $dark-elem-bg;
    }
  }
}
</style>
