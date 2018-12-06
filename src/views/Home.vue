<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <SteemFeed/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import SteemFeed from '@/components/SteemFeed.vue'

export default {
  name: 'home',
  components: {
    HelloWorld,
    SteemFeed
  }
}
</script>
