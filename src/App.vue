<template>
  <div id="app">
    <h1>Vue.js Image Editor</h1>
    <ImageEditor />
  </div>
</template>

<script>
import ImageEditor from './components/ImageEditor';

export default {
  name: 'App',
  components: {
    ImageEditor,
  },
};
</script>

<style>
body {
  background-color: #333;
  margin: 0;
  padding: 0;
}

h1 {
  color: white;
}

#app {
  position:relative;
  width: 100vw;
  height: 100vh;
  color: #2c3e50;
  background-color: #333;
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  
}
</style>
