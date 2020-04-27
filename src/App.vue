<template>
  <div id="app">
    <template v-if="cordovaReady">
      <router-view />
    </template>
  </div>
</template>

<script>
import { defineComponent, ref } from '@vue/composition-api'

export default defineComponent({
  setup(){
    const cordovaReady = ref(false)
    function cordovaInit(){
      cordovaReady.value = true
    }

    document.addEventListener("deviceready", cordovaInit, false);

    return {
      cordovaReady
    }
  }
})
</script>

<style lang="scss">
html,body{
  overscroll-behavior-y: none;
  padding: 0;
  margin: 0;
  *{
    outline: none;
  }
}
#app{
  padding: 10px;
  font-size: 20px;
  color: #707070;
}
</style>
