<template>
  <div id="app">
    <h3>default</h3>
    <Example></Example>
  </div>
</template>
<script>
import Example from './example/Example';

export default {
  name: 'app',
  components: {
    Example
  }
}
</script>

<style >
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
