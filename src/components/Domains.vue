<template>
  <div>
    <h1>Domains</h1>
    <ul>
      <li v-for="(domain, index) in domains" v-bind:key="index">
        {{ domain.title }}
      </li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Domains",
  data() {
    return {
      domains: null
    };
  },
  mounted() {
    axios.get("http://localhost:3000/domains/").then(response => {
      this.domains = response.data;
    });
  }
};
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: block !important;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
