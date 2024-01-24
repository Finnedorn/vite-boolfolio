<template>
    <form @submit.prevent="submitForm">
        <div class="mb-3">
            <label for="name" class="form-label">Nome</label>
            <input type="text" class="form-control" id="name" aria-describedby="nameHelp" v-model="name">
            <div id="name" class="form-text">Inserisci il tuo nome</div>
        </div>
        <div class="mb-3">
            <label for="email" class="form-label">Email</label>
            <input type="email" class="form-control" id="email" aria-describedby="emailHelp" v-model="email">
            <div id="emailHelp" class="form-text">Inserisci la tua mail</div>
        </div>
        <div class="mb-3">
            <label for="address" class="form-label">Indirizzo</label>
            <input type="text" class="form-control" id="address" aria-describedby="addressHelp" v-model="address">
            <div id="address" class="form-text">Inserisci il tuo indirizzo</div>
        </div>
        <div class="mb-3">
            <label for="message" class="form-label">Messagio</label>
            <textarea  class="form-control" id="message" aria-describedby="message" v-model="message">
            </textarea>
            <div id="message" class="form-text">Inserisci un tuo messaggio</div>
        </div>
        <button type="submit" class="btn btn-secondary">Cancella</button>
        <button type="submit" class="btn btn-primary mx-2 ">Invia</button>
    </form>
</template>
  
<script>
// import axios from "axios";
import axios from "axios";
import { store } from "../assets/data/store";
export default {
    name: 'ContactForm',
    components: {
    },
    data() {
        return {
            store,
            name: '',
            email: '',
            address: '', 
            message: '',
        };
    },
    methods: {
        submitForm() {
            const data= {
                name: this.name,
                email: this.email,
                address: this.address,
                message: this.message,
            };

            axios.post(this.store.apiUrl+'/contacts', data).then((res)=>{
                this.name= '';
                this.email= '';
                this.address= '';
                this.message= '';
            }).catch((err)=>{
                console.log('error', err);
            })
        }
    },
    mounted() {

    }
}
</script>
  
<style lang="scss" scoped>
// @use "./assets/style/partials/variables" as *;
</style>