<template>
    <h1>
        Hello
    </h1>
</template>
  
<script>
import axios from "axios";
import { store } from "../assets/data/store";
export default {
    name: 'AppHome',
    components: {
        
    },
    data() {
        return {
            store,
            projects: [],
            currentPage: 1,
            lastPage: 0,
        };
    },
    methods: {
       
    },
    mounted() {
        
    }
}
</script>
  
<style lang="scss" scoped>
//   @use "./assets/style/partials/variables" as *;
</style>