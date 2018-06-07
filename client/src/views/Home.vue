<template>
  <div class="home">
    <getToken/>
    <postImage/>
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import getToken from '@/components/getToken.vue'
import postImage from '@/components/postImage.vue'
export default {
  name: 'home',
  components: {
    HelloWorld,
    getToken,
    postImage
  }
}
</script>
