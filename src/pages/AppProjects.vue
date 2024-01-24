<template>
    <h1>
        Projects:
    </h1>
    <div class="row m-3">
        <CardComponent v-for="(project, index) in store.projects" :key="index"
            :link="{ name: 'project-info', params: { slug: project.slug } }" :source="store.imgBasePath + project.preview"
            :title="project.project_title" :subtitle="project.repo_name" :badges="project.technologies" />
    </div>


    <label for="category" class="form-label">Categoria</label>
    <select class="form-control" id="category" name="category" v-model="selectedCategory" @change="filterProject">
        <option value="" selected>Seleziona la Categoria</option>
        <option v-for="category in store.categories" :value="category.id" :key="category.id">
            {{ category.name }}
        </option>
    </select>
    
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
            selectedCategory: null
        };
    },
    methods: {
        getAllProjects() {
            axios.get(this.store.apiUrl + "/projects", { params: { page: this.currentPage } }).then((res) => {
                this.store.projects = res.data.results.data;
                // console.log(this.store.projects);
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
        },
        getCategory() {
            axios.get(this.store.apiUrl + "/categories").then((resp)=>{
            console.log(resp.data);
            this.store.categories = resp.data.results;
            })
        },
        filterProject() {

            if(this.selectedCategory == "") {

                this.getAllProjects();

            } else {

                axios.get(this.store.apiUrl + "/projects", { params: {category: this.selectedCategory} }).then((res) => {
                console.log(res.data);
                this.store.projects = res.data.results;
                });
            }
            // console.log(this.selectedCategory);
        }
    },
    mounted() {
        this.getAllProjects();
        this.getCategory();
    }
}
</script>
  
<style lang="scss" scoped></style>