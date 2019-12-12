<template>
  <div>
    <h1>Domain</h1>
    <center>
      <input v-model="host" placeholder="Enter domain" />
      <button v-on:click="search">Search</button>
      <h2>{{response.title}}</h2>
      <img v-bind:src="response.logo" />
      <table v-if="response">
        <tr>
          <td>
            <b>Is Down</b>
          </td>
          <td>{{response.is_down}}</td>
        </tr>
        <tr>
          <td>
            <b>Servers Changed</b>
          </td>
          <td>{{response.servers_changed}}</td>
        </tr>
        <tr>
          <td>
            <b>Ssl Grade</b>
          </td>
          <td>{{response.ssl_grade}}</td>
        </tr>
        <tr>
          <td>
            <b>Previous ssl grade</b>
          </td>
          <td>{{response.previous_ssl_grade}}</td>
        </tr>
        <tr>
          <td>
            <b>Servers</b>
          </td>
          <td>
            <table
              class="table-server"
              v-for="(server, index) in response.servers"
              v-bind:key="index"
            >
              <tr>
                <td>
                  <b>Address</b>
                </td>
                <td>{{ server.address }}</td>
              </tr>
              <tr>
                <td>
                  <b>Ssl grade</b>
                </td>
                <td>{{ server.ssl_grade }}</td>
              </tr>
              <tr>
                <td>
                  <b>Country</b>
                </td>
                <td>{{ server.country }}</td>
              </tr>
              <tr>
                <td>
                  <b>Owner</b>
                </td>
                <td>{{ server.owner }}</td>
              </tr>
            </table>
          </td>
        </tr>
      </table>
       <p v-else>Not found domain</p>
    </center>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "DomainSearch",
  data() {
    return {
      host: "",
      response: ""
    };
  },
  methods: {
    search: function() {
      axios
        .get("http://localhost:3000/domains/host=" + this.host)
        .then(response => {
          this.response = response.data;
        });
    }
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
.table-server {
  border-bottom: 1.5px solid #42b983;
}
table, tr, td {
  text-align: center;
}
</style>
