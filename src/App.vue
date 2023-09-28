<template>
  <div id="app">
    <HelloWorld>
      <template #example>
        <h2 v-if="loaded">
          <!-- content needs to access a variable -->
          <span>After {{ foobar }}</span>
        </h2>

        <!-- h2 does not work because it is the same DOM element as in the default slot content. h1 is working because it is a different element -->
        <!-- <h1 v-if="loaded"><span>After {{ foobar }}</span></h1> -->
      </template>
    </HelloWorld>
    {{ loaded }}
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';

export default {
  name: 'App',
  components: {
    HelloWorld,
  },
  data() {
    return {
      loaded: false,
      foobar: 123,
    };
  },
  mounted() {
    window.setTimeout(() => {
      console.log('LOADED CHANGED');
      this.loaded = true;
    }, 3000);
  },
};
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
