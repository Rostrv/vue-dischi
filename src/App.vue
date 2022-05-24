<template>
  <div id="app">
    <SiteHeader/>
    <SiteMain/>
  </div>
</template>

<script>
import SiteHeader from './components/SiteHeader.vue'
import SiteMain from './components/SiteMain.vue'


export default {
  name: 'App',
  components: {
    SiteHeader,
    SiteMain,
  }
}
</script>

<style lang="scss">
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

img{
  width: 100%;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
 min-height: 100vh;
  background-color: #1e2c3a;
}
</style>
