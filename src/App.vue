<template>
  <div id="app">
    <Header />
    <SearchBox v-on:do-search="doSearch"/>
    <Sibling v-bind:req="tower.res" 
      v-on:clear-req-header="clearReqHeader"
      v-on:clear-req-body="clearReqBody" />
  </div>
</template>

<script>
import Header from './components/layout/Header';
import SearchBox from './components/SearchBox';
import Sibling from './components/Sibling';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    Header,
    SearchBox,
    Sibling
  },
  data() {
    return {
      tower: {
          res: {
            header: "empty",
            body: "empty"
          }
        }
    }
  },
  methods: {
    doSearch(searchQuery) {
      // do search
      console.log(searchQuery.q);

      axios.get("http://jsonplaceholder.typicode.com/users?_limit=3")
        .then(res => {
          console.log(res); 
          this.tower.res.header = res.headers;
          this.tower.res.body = res.data;
        })
        .catch(err => console.log(err));
    },

    clearReqHeader() {
      this.tower.res.header = 'cleared';
    },

    clearReqBody() {
      this.tower.res.body = 'cleared';
    }
  }
}
</script>

<style>
  * { 
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  body {
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
  }
</style>
