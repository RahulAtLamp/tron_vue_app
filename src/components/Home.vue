<template>
  <div class="home">
    <h1>Transactions</h1>
    <div class="container">
      <div class="all_data">
        <div class="single0">No</div>
        <div class="single1">Timestamp</div>
        <div class="single2">Transaction ID</div>
        <div class="single3">Symbol</div>
        <div class="single4">To</div>
        <div class="single5">From</div>
        <div class="single6">Amount</div>
      </div>
      <div v-for="datas in info" v-bind:key="datas">
        <div v-for="(data, index) in datas" class="all_data" v-bind:key="data">
          <div v-if="data[6]='sent'" style="background-color:#ccc; width:100%; display: flex;">
            <div class="single0">
              {{ Number(index + 1) }}
            </div>
            <div class="single1">
              {{data[0]}}
            </div>
            <div class="single2">
              {{data[1]}}
            </div>
            <div class="single3">
              {{data[2]}}
            </div>
            <div class="single4">
              {{data[3]}}
            </div>
            <div class="single5">
              {{data[4]}}
            </div>
            <div class="single6">
              {{Number(data[5]/1000000)}}
            </div>
          </div>
          <div v-else style="background-color:white; width:100%; display: flex;">
            <div class="single1">
              {{data[0]}}
            </div>
            <div class="single2">
              {{data[1]}}
            </div>
            <div class="single3">
              {{data[2]}}
            </div>
            <div class="single4">
              {{data[3]}}
            </div>
            <div class="single5">
              {{data[4]}}
            </div>
            <div class="single6">
              {{Number(data[5]/1000000)}}
            </div>
          </div>
        </div>
      </div>
    </div>
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
  created() {
    this.interval = setInterval(() => {
      this.fetchTransactions();
    }, 3000);
  },
  methods: {
    fetchTransactions() {
      axios.get('http://127.0.0.1:5000/show').then((res) => {
        this.info = [];
        this.info.push(res.data.data);
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

  .single0{
    width:30px;
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
