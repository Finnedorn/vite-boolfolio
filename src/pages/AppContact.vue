<template>
    <div class="p-3 w-75 m-auto mt-3">
        <h1>Contattami</h1>
        <ContactForm/>
    </div>
</template>
  
<script>
import axios from "axios";
import { store } from "../assets/data/store";
import ContactForm from "../components/ContactForm.vue";
export default {
    name: 'AppContact',
    components: {
        ContactForm
    },
    data() {
        return {
            store,
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