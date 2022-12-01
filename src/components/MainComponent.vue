<template>
  <div id="container">
    <p class="text" v-on:click="alert">Hallo</p>
    <ul>
      <li>
        <p class="text" v-for="item in data" :key="item.code">
          {{ data != [] ? item.currency : "" }}
        </p>
      </li>
    </ul>
  </div>
</template>
<script>
import { onMounted, ref } from "vue";
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
    alert: function () {
      alert("blah");
    },
  },

  setup() {
    const data = ref(null);
    const getData = () => {
      axios
        .get(Api)
        .then((response) => {
          data.value = response.data[0].rates;
        })
        .catch((error) => {
          console.log(error);
        });
    };
    onMounted(async () => {
      await getData();
    });

    return { data };
  },
};
</script>
