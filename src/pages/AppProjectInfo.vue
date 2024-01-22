<template>
    <h1>single project</h1>
    <div v-if="project">
        <h1>{{ project.project_title }}</h1>
        <h4>{{ project.repo_name }}</h4>
        <h6>{{ project.repo_link }}</h6>
        <h6>{{ project.category.name }}</h6>
        <div>
            <h6>Tecnologie:</h6>
            <div v-for="technology in project.technologies">
                {{ technology.name }}
            </div>
        </div>
        <div class="w-25">
            <img :src="store.imgBasePath+project.preview"  :alt="project.project_title">
        </div>
        <p>
            {{ project.description }}
        </p>
    </div>
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
            axios.get(this.store.apiUrl + "/projects/" + this.$route.params.slug).then((res)=>{
                console.log(res.data);
                if(res.data.results) {
                    this.project=res.data.results
                }else {
                    this.$router.push({name: 'not-found'})
                }
            })
        }
    },
    mounted() {
        this.getProjectInfo();
    }
}
</script>
  
<style lang="scss" scoped>
// @use "./assets/style/partials/variables" as *;
</style>