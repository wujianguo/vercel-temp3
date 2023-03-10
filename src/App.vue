<script setup lang="ts">
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />
    <p>{{ data.data }}</p>
    <p>{{ data2.data }}</p>
    <div class="wrapper">
      <HelloWorld msg='Hello World' />
    </div>
  </header>

  <main>
    <TheWelcome />
  </main>
</template>

<script lang="ts">
import axios from 'axios'
export default {
  data() {
    return {
      data: { data: 'Loading...'},
      data2: { data: 'Loading2...'}
    }
  },
  mounted() {
    axios.get('/api/hello').then((response) => {
      this.data = response.data
    })
    axios.get('/api/hello/foo').then((response) => {
      this.data2 = response.data
    })
  }
}
</script>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
