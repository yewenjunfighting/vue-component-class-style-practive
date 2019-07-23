<template>
    <div class="blogpost">
        <h2>{{ post.title }}</h2>
        <p>{{ post.body }}</p>
        <p class="meta">Written by {{ post.author }} on {{ date }}</p>             
    </div>  
</template>

<script lang="ts">
import { Component, Prop, Vue, Watch } from 'vue-property-decorator';

export interface Post {
    title: string;
    body: string;
    author: string;
    datePosted: Date;
}

@Component
export default class Blog extends Vue {
    @Prop() private post!: Post;
    @Watch('post', { immediate: true })
    // 当监听的属性是对象时, oldVal是undefined
    private onPostChange(val: Post, oldVal: Post) {
        console.log('监听Post的变换');
        console.log(val, oldVal);
    }

    private created() {
        console.log('son component created');
    }

    private mounted() {
        // console.log(this.post);
        // console.log(this.$el)
    }

    private updated() {
        console.log('son component update');
    }

    // 计算属性
    get date() {
        return `${this.post.datePosted.getDate()}/${this.post.datePosted.getMonth()}/${this.post.datePosted.getFullYear()}`;
    }
}

</script>
