<template>
  <div class="home">
    <HelloWorld v-on:fromSon="receiver" msg="Hello World"/>
    <Blog v-for="post in posts"  :post="post" :key="post.title"/>
    <el-button type="primary" v-on:click="changePosts">watch测试</el-button>
   </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import HelloWorld from '@/components/HelloWorld.vue'; // @ is an alias to /src
import Blog, { Post } from '@/components/Blog.vue';

@Component({
  components: {
    HelloWorld,
    Blog,
  },
})
export default class Home extends Vue {
  // 相当于原先的data
  private posts: Post[] = [
    {
        title: 'vue',
        body: '深入浅出vue.js',
        author: '博文',
        datePosted: new Date(),
    },
    {
        title: 'JavaScript高级程序设计',
        body: '这是一本很好的JS入门教程',
        author: '译者: 李松峰',
        datePosted: new Date(),
    },
    {
        title: '你不知道的JS',
        body: '还没又读完',
        author: '译者是两位大学生',
        datePosted: new Date(),
    },
  ];

  public receiver(info: string): void {
    // console.log(`${info} from son component`);
  }

  private mounted() {
    // console.log(this.$el)
  }

  private changePosts(event: Event): void {
    console.log('click');
    const index: number = Math.floor(Math.random() * 3);
    this.posts[index].title = this.posts[index].title.split('').reverse().join('');
  }
  private updated(): void {
    console.log('update')
  }
}
</script>
