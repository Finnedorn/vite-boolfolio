<template>
    <form @submit.prevent="submitForm">
        <p v-if="errors.legth">
            <b>Correggi i seguenti errori per continuare:</b>
            <ul>
                <li v-for="error in errors">{{ error }}</li>
            </ul>
        </p>
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
            <label for="message" class="form-label">Messaggio</label>
            <textarea  class="form-control" id="message" aria-describedby="message" v-model="message">
            </textarea>
            <div id="message" class="form-text">Inserisci un tuo messaggio</div>
        </div>
        <button type="submit" class="btn btn-secondary">Cancella</button>
        <button type="submit" class="btn btn-primary mx-2 ">Invia</button>
    </form>
</template>
  
<script>
import axios from "axios";
import { store } from "../assets/data/store";
export default {
    name: 'ContactForm',
    components: {
    },
    data() {
        return {
            store,
            name: null,
            email: null,
            address: null, 
            message: null,
            errors: [],
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

            if(!data.name || !data.email || !data.address || !data.message) {
                if(!data.name) {
                    this.errors.push('Il campo nome è obbligatorio');
                }
                if(!data.email) {
                    this.errors.push('Il campo email è obbligatorio');
                }
                if(!data.address) {
                    this.errors.push('Il campo indirizzo è obbligatorio');
                }
                if(!data.message) {
                    this.errors.push('Il campo messaggio è obbligatorio');
                }
                return this.errors;
            }

            axios.post(this.store.apiUrl+'/contacts', data).then((res)=>{
                this.name= null;
                this.email= null;
                this.address= null;
                this.message= null;
            }).catch((err)=>{
                console.log('error', err);
            });
        }
    },
    mounted() {
    }
}
</script>
  
<style lang="scss" scoped>
// @use "./assets/style/partials/variables" as *;
</style>