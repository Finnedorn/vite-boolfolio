<template>
    <h1>
        Projects:
    </h1>
    <ul>
        
    </ul>
</template>
  
<script>
import axios from "axios";
import { store } from "../assets/data/store";
export default {
    name: 'AppProjects',
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
        getAllProjects() {
            axios.get(store.apiUrl + "/projects", { params: { page: this.currentPage } }).then((res) => {
                console.log(res.data);
                this.projects = res.data.results.data;
                console.log(this.projects);
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
  
<style lang="scss" scoped></style>