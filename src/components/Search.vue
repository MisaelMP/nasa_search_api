<template>
  <div class="search">
    <h1>{{ msg }}</h1>
    <form class="search_form" v-on:submit.prevent="getResult(query)">
      <input type="text" placeholder="Find..." v-model="query"  />
      <button><font-awesome-icon icon="search" /></button>
    </form>
    <div class="results" v-if="results">
      <div v-for="result in results">
        <img v-bind:src="result.links[0].href"  />
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'Search',
  data () {
    return {
      msg: 'Nasa Search',
      query: '',
      results: ''
    }
  },
  methods: {
    getResult(query) {
      axios.get(`https://images-api.nasa.gov/search?q= ${query} &media_type=image`).then(response => {
        console.log(response.data.collection.items);
        this.results = response.data.collection.items;
      });
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import url('https://fonts.googleapis.com/css?family=Anton|Oswald');

h1, h2 {
  font-weight: normal;
  font-size: 5vw;
  font-family: 'Anton', sans-serif;
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
.results img {
  height: 300px;
  margin: 1em;
}


form {
  display: flex;
  justify-content: center;
  margin-bottom: 4em;
}

/* Style the search field */
form.search_form input[type=text] {
  margin: 0;
  padding: 10px;
  font-size: 17px;
  border: 1px solid grey;
  border-radius: .5em 0 0 .5em;
  float: left;
  max-width: 20%;
  background: #f1f1f1;
}

/* Style the submit button */
form.search_form button {
  float: left;
  width: 5%;
  padding: 10px;
  background: #2c3e50;
  color: white;
  font-size: 17px;
  border: 1px solid #5f7583;
  border-left: none; /* Prevent double borders */
  border-radius: 0 .5em .5em 0em;

  cursor: pointer;
}

form.search_form button:hover {
  background: #5f7583;
}

/* Clear floats */
form.search_form::after {
  content: "";
  clear: both;
  display: table;
}
</style>
