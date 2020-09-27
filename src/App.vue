<template>
  <div id="app">
    <header>Header</header>
    <div class="main">
      <transition name="slide" mode="out-in">
        <router-view />
      </transition>
    </div>
    <footer>
      <router-link exact to="/" class="item">Home</router-link>
      <router-link exact to="/about" class="item">About</router-link>
    </footer>
  </div>
</template>

<script>
export default {
  name: "App",
  watch: {
    $route(to, from) {
      // const toDepth = to.path.split("/");
      // const fromDepth = from.path.split("/");
      const toDepth = to.path;
      const fromDepth = from.path;
      console.log(toDepth, fromDepth);
    },
  },
};
</script>

<style lang="scss">
$primary: #14213D;
$accent: #FCA311;
$dark: #000000;
$grey: #E5E5E5;
$white: #fff;
* {
  margin: 0;
  padding: 0;
  box-shadow: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: $dark;
  display: grid;
  grid-template-rows: 10vh 80vh 10vh;
}

body {
  font-size: 10px;
}

a {
  text-decoration: none;
  color: inherit;
}

.main {
  background: $white;
}

header {
  background: $primary;
  color: $white;
  display: flex;
  align-items: center;
  padding: 0 1rem;
  font-size: 1.5rem;
}

footer {
  background: $primary;
  color: $white;
  padding: 0.2rem 20vw;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-column-gap: 0.2rem;
  justify-content: center;
  font-size: 1.2rem;

  .item {
    display: flex;
    align-items: center;
    justify-content: center;
    transition: all 0.3s;
    &:hover {
      background: darken($accent, 20%);
    }
    &.router-link-active {
      border-bottom: 1px solid $accent;
    }
  }
}

.slide {
  &-enter-active,
  &-leave-active {
    transition: opacity 0.8s, transform 0.8s;
  }

  &-enter,
  &-leave-to {
    opacity: 0;
    transform: translateX(-30%);
  }
}
</style>
