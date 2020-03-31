<template>
  <div id="app">
  <swiper>

  </swiper>
    <swiper_item></swiper_item>
  </div>
</template>

<script>
import {swiper,swiper_item} from './components/common/swiper/index'

export default {
  name: 'App',
  components: {
    swiper,
    swiper_item
  }
}



</script>

<style>
*,
body{
  margin: 0;
  padding: 0;
  text-align: center;
}
</style>
