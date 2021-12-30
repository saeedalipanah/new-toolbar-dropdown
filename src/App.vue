<template>
  <div class="app">
    <Toolbar />
  </div>
</template>

<script>
import Toolbar from './components/Toolbar.vue'
export default {
  name: 'App',
  components:{
    Toolbar,
  }
}
</script>

<style lang="scss">
// 
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>
