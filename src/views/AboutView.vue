<template>
  <div class="about">
    <h1>This is an about page</h1>
    <div>{{info.date}}</div>
  </div>
</template>
<script>
import axios from 'axios';

export default {
  name: 'LandingPage',
  data() {
    return {
      msg: 'Welcome to Your Vue.js App',
      info: [],
    };
  },
  mounted() {
    this.fetchTransactions();
  },
  methods: {
    fetchTransactions() {
      axios.get('http://127.0.0.1:5000/daily').then((res) => {
        this.info.push(res.data);
        // console.log(res.data);
      }).catch();
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .all_data{
    display: flex;
    font-size: 13px;
    border: 1px solid #121212;
  }

  .single1{
    width: 120px;
  }
  .single2{
    width: 500px;
    overflow: hidden;
    text-overflow: ellipsis;
  }
  .single3{
    width: 50px;
    overflow: hidden;
    text-overflow: ellipsis;
  }
  .single4{
    width: 320px;
    overflow: hidden;
    text-overflow: ellipsis;
  }
  .single5{
    width: 320px;
    overflow: hidden;
    text-overflow: ellipsis;
  }
</style>
