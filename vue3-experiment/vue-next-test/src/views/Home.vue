<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
	  <teleport to="#modal-wrapper">
		  <HelloWorld msg="Welcome to Your Vue.js App"/>
	  </teleport>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'Home',
  components: {
    HelloWorld
  }
}
</script>
