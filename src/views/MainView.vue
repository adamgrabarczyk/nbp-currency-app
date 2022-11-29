<template>
  <main-component />
</template>

<script lang="ts">
import { defineComponent } from "vue";

import MainComponent from "../components/MainComponent.vue";

export default defineComponent({
  name: "MainView",

  components: {
    MainComponent,
  },
});
</script>
