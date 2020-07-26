<template>
  <v-app>
    <div id="app">
      <Navbar />
      <div class="container">
        <router-view />
    </div>
  </div>
  </v-app>
</template>

<script>
import Navbar from './components/Navbar';

export default {
  name: 'App',

  components: {
    Navbar
  },
};
</script>
