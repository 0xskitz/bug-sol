<template>
  <!-- <RunningMaurice /> -->
  <RunningMaurice />
  <RunningMaurice />
  <RunningMaurice />
  <RunningMaurice />
  <MauriceComponent />
  <RunningMaurice />
  <RunningMaurice />
  <RunningMaurice />
  <RunningMaurice />
</template>

<script>
import MauriceComponent from './components/MauriceComponent.vue'
import RunningMaurice from './components/RunningMaurice.vue';

export default {
  name: 'App',
  components: {
    RunningMaurice,
    MauriceComponent
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
