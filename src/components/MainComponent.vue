<template>
  <div id="container">
    <p class="text" v-on:click="handleInput">Hallo</p>
    <ul>
      <li>
        <p class="text" v-for="item in results" :key="item.code">
          {{ results != [] ? item.currency : "" }}
        </p>
      </li>
    </ul>
  </div>
</template>
<script>
import { onMounted } from "vue";
import axios from "axios";

const Api = "http://api.nbp.pl/api/exchangerates/tables/b";
export default {
  name: "nbpCurrency",
  data() {
    return {
      results: [],
    };
  },
  methods: {
    handleInput: function () {
      axios
        .get(Api)
        .then((response) => {
          console.log(response.data[0].rates[0].code);
          this.results = response.data[0].rates;
        })
        .catch((error) => {
          console.log(error);
        });
    },

    alert: function () {
      alert("blah");
    },
  },
};
</script>
