<template>
    <h1>
        Projects:
    </h1>
    <div class="row m-3">
        <CardComponent
        v-for="(project, index) in store.projects"
        :key="index"
        :source="store.imgBasePath+project.preview"
        :title="project.project_title"
        :subtitle="project.repo_name"
        :badges="project.technologies"
        />
    </div>
    <ul>
        <li v-for="project in store.projects">
            <router-link  :to="{name: 'project-info', params:{ slug: project.slug }}">
            {{ project.project_title }}
            </router-link>
        </li>
    </ul>
    
</template>
  
<script>
import axios from "axios";
import { store } from "../assets/data/store";
import CardComponent from "@/components/CardComponent.vue";
export default {
    name: 'AppProjects',
    components: {
    CardComponent,
},
    data() {
        return {
            store,
            currentPage: 1,
            lastPage: 0,
        };
    },
    methods: {
        getAllProjects() {
            axios.get(this.store.apiUrl + "/projects", { params: { page: this.currentPage } }).then((res) => {
                this.store.projects = res.data.results.data;
                console.log(this.store.projects);
                this.currentPage = res.data.results.current_page;
                this.lastPage = res.data.results.last_page;
            });
        },
        nextPage() {
            this.currentPage = this.currentPage + 1;
            this.getAllProjects()
        },
        previousPage() {
            this.currentPage = this.currentPage - 1;
            this.getAllProjects()
        }
    },
    mounted() {
        this.getAllProjects();
    }
}
</script>
  
<style lang="scss" scoped>
</style>