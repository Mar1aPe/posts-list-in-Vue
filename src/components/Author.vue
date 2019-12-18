<template>
  <h1>{{author}}</h1>
</template>

<script>
import axios from "axios";

export default {
  name: "Author",
  props: {
    id: String
  },
  data() {
    return {
      author: ""
    };
  },
  created() {
    axios
      .get(`http://jsonplaceholder.typicode.com/posts/${this.props.id}`)
      .then(response => {
        // this.author = response.data;
        /* eslint-disable no-console */
        console.log(response);
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
