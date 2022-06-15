<template>
  <div class="home">
    <LandingPage msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
// @ is an alias to /src
import LandingPage from '@/components/Home.vue';

export default {
  name: 'HomeView',
  components: {
    LandingPage,
  },
};
</script>
