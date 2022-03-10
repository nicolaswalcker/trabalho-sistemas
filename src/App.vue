<template>
  <div id="app">
    <ParticlesContainer />
    <router-view />
  </div>
</template>
<script>
import ParticlesContainer from './components/ParticlesContainer.vue';
export default {
  name: 'App',
  components: {
    // eslint-disable-next-line vue/no-unused-components
    ParticlesContainer,
  }
};
</script>

