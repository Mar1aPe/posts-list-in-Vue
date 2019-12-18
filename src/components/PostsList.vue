<template>
  <div id="posts-list" >
    <ul class="list" v-if="posts && posts.length" >
      <li class="post" v-for="post of posts" v-bind:key="post.id">
        <h4>{{post.title}}</h4>

        <span v-if="!readMoreActivated">{{post.body.slice(0, post.body.length/2)}}</span>
        <br />
        <a class v-if="!readMoreActivated" @click="activateReadMore" href="#">Read more...</a>
        <span v-if="readMoreActivated" v-html="post.body"></span>
        <p>
          {{authors.filter(author => {
          return author.id== post.userId ? author.name : '' ;
          })}}
        </p>

        <!-- <Author v:bind:id="post.userId" /> -->
      </li>
    </ul>
    <ul class="pagination"></ul>
  </div>
</template>

<script>
import axios from "axios";
import Author from "./Author.vue";

export default {
  name: "PostsList",

  components: Author,
  data() {
    return {
      posts: [],
      authors: [],
      readMoreActivated: false
    };
  },

  methods: {
    activateReadMore() {
      this.readMoreActivated = !this.readMoreActivated;
    }
  },

  created() {
    axios.get("http://jsonplaceholder.typicode.com/posts").then(response => {
      this.posts = response.data;
      /* eslint-disable no-console */
      console.log(response.data);
      /* eslint-disable no-console */
    });
    axios.get("http://jsonplaceholder.typicode.com/users").then(response => {
      this.authors = response.data;
      /* eslint-disable no-console */
      console.log(response.data);
      /* eslint-disable no-console */
    });
  }
};
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
