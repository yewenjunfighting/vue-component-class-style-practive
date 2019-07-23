<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <el-button type="primary" v-on:click="communication">{{ info }}</el-button>
  </div>
</template>

<script lang="ts">
// 属性修饰符
import { Component, Prop, Vue, Emit } from 'vue-property-decorator';
import { Button, Select } from 'element-ui';

Vue.component(Button.name, Button);

@Component
export default class HelloWorld extends Vue {
  // !:非空断言参数，表示一定会有值
  private info: string = '父子组件通信测试';
  @Prop({default: 'Hello World'}) private msg!: string;

  // 用@Emit进行父子组件通信
  @Emit('fromSon')
  private communication(): string {
    return this.info;
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
