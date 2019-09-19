<template>
  <div id="app">
    <header>
      <span class="logo">Ipsums of the World</span>
    </header>
    <nav>
        <ul class="nav">
          <li>
            <router-link to="/">Home</router-link>
          </li>
          <li>
            <router-link to="/cat">Cat Ipsum</router-link>
          </li>
          <li>
            <router-link to="/hipster">Hipster Ipsum</router-link>
          </li>
          <li>
            <router-link to="/cupcake">Cupcake Ipsum</router-link>
          </li>
        </ul>
      </nav>
    <main>
      <router-view></router-view>
    </main>
  </div>
</template>

<script>
import Vue from "vue";
import VueRouter from "vue-router";
import Home from "./components/Home.vue";
import Cat from "./components/Cat.vue";
import Hipster from "./components/Hipster.vue";
import Cupcake from "./components/Cupcake.vue";

Vue.use(VueRouter);

const router = new VueRouter({
  routes: [
    { path: "/", component: Home, meta: { title: 'Home | Ipsums of the World'} },
    { path: "/cat", component: Cat, meta: { title: 'Cat Ipsum | Ipsums of the World'} },
    { path: "/hipster", component: Hipster, meta: { title: 'Hipster Ipsum | Ipsums of the World'} },
    { path: "/cupcake", component: Cupcake, meta: { title: 'Cupcake Ipsum | Ipsums of the World'} }
  ]
});

export default {
  router,
  watch: {
    $route: function(to) {
      // $nextTick = DOM updated
      this.$nextTick(function() {
        // Change document title
        document.title = to.meta.title;
      });
    }
  },
};
</script>

<style>
.router-link-exact-active {
  color: #000;
  text-decoration: none;
}

body {
  margin: 0;
  padding: 0;
}

#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: grid;
  grid-template-columns: 15rem 1fr;
  grid-template-areas:
    "header header"
    "nav main";
  line-height: 1.6;
}

header {
  grid-area: header;
  min-height: 4rem;
  background-color: #096073;
  display: flex;
  align-items: center;
}

header .logo {
  color: #fff;
  font-size: 2rem;
  text-decoration: none;
  font-weight: bold;
}

nav {
  grid-area: nav;
  width: 15rem;
}

nav ul {
  list-style: none;
  margin: 2rem 0 0;
  padding: 0;
  font-size: 110%;
  line-height: 2;
}

nav a {
}

main {
  grid-area: main;
}

main p {
  max-width: 80ch;
}

nav a,
main a {
  color: #096073;
  font-weight: bold;
}

header,
nav,
main {
  padding: 1rem;
}
</style>
