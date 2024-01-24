<template>
    <div v-if="project">
        <h1>{{ project.project_title }}</h1>
        <div class="w-25">
            <img :src="store.imgBasePath+project.preview"  :alt="project.project_title">
        </div>
        <h4>{{ project.repo_name }}</h4>
        <h6>{{ project.repo_link }}</h6>
        <h6>{{ project.category.name }}</h6>
        <div>
            <h6>Tecnologie:</h6>
            <div v-for="technology in project.technologies">
                {{ technology.name }}
            </div>
        </div>
        <p>
            {{ project.description }}
        </p>
    </div>
    <router-link :to="{name: 'project-info', params: {slug: 'boolflix'}}">
        linkone!!!
    </router-link>
    
</template>

<script>
import axios from "axios";
import { store } from "../assets/data/store";
export default {
    name: 'AppProjectInfo',
    components: {
    },
    data() {
        return {
            store,
            project: null,

        };
    },
    methods: {
        getProjectInfo() {
            console.log('ciao');
            // lo slug che uso viene passato dal routerlink tramite la variabile nativa $route
            axios.get(this.store.apiUrl + "/projects/" + this.$route.params.slug).then((res)=>{
                // console.log(res.data);
                if(res.data.results) {
                    this.project=res.data.results
                }else {
                    this.$router.push({name: 'not-found'})
                }
            })
        },
        
    },
    mounted() {
        this.getProjectInfo();
        // this.$watch(() => this.$route.params, (toParams, previousParams) => {
        //     if(toParams !== previousParams){
        //         this.getProjectInfo();
        //     }
        // })
    }
}
</script>
  
<style lang="scss" scoped>
// @use "./assets/style/partials/variables" as *;
</style>