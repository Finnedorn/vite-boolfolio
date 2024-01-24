<template>
  <HeaderComponent/>
  <router-view :key="$route.path"></router-view>
</template>

<script>
import axios from "axios";
import { store } from "./assets/data/store";
import HeaderComponent from "./components/HeaderComponent.vue";
export default {
  name: 'App',
  components: {
    HeaderComponent
  },
  data() {
    return {
      
    };
  },
  methods: {
    
  },
  mounted() {
    
  }
}
</script>

<style lang="scss" scoped>
// @use "./assets/style/partials/variables" as *;
</style>
