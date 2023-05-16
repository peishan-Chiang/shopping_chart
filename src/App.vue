<script >

import { RouterLink, RouterView } from 'vue-router'
import BuyChart from './views/BuyChart.vue';
export default {
  components: {
    BuyChart

  },
  data() {
    return {

    }
  },
  methods: {
    fn() {


    }
  },
  // 生命週期
  mounted() {
    // this.fn();
    

  }
}
</script>

<template>
  <header>

    <BuyChart />
    <div class="wrapper">


      <nav>

        <!-- <RouterLink to="/">Home</RouterLink> -->
        <!-- <RouterLink to="/about">About</RouterLink> -->
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
  flex-direction: column;
  display: flex;
  justify-content: center;
  align-items: center;
}



nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

mark {
  background: orange;
  color: black;
}
</style>
