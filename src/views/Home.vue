<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
<<<<<<< HEAD
    <HelloWorld msg="Hello World"/>
=======
    <HelloWorld msg="Welcome to Your Vue.js + TypeScript App"/>
    <p>git pull 测试</p>
>>>>>>> 12939f54da99bab16a77d15819303c790eff068e
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import HelloWorld from '@/components/HelloWorld.vue'; // @ is an alias to /src

// Vue组件的ts写法
@Component({
  components: {
    HelloWorld,
  },
})
export default class Home extends Vue {}
</script>
