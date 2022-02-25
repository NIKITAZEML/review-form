<template>
  <div id="app">
      <auth-window></auth-window>
  </div>
</template>

<script>

import AuthWindow from "./components/AuthWindow";
export default {
  name: 'App',
  components: {
      AuthWindow
  }
}
</script>

<style>
    @import "./assets/null.css";
</style>
