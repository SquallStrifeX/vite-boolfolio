<script >
import axios from 'axios';
import { store } from '../store.js';
import Project from '../components/Project.vue';

export default {
    components: {
        Project,
    },
    data() {
        return {
            store,
            types:[],
            projects: [],
        
        }
    },
    created() {
        this.getProjects();
        this.getTypes();
    },
    methods: {
        getProjects() {
            
            axios.get(`${this.store.endpoint}/api/projects/type/${this.$route.params.slug}`).then((response) => {
                // Applichiamo il valore della richiesta all array
                this.projects = [];
                this.projects = response.data.results;
            })
        },
        getTypes(){
            axios.get(`${this.store.endpoint}/api/types`).then((response) =>{
                 // Applichiamo il valore della richiesta all array
                this.types = response.data.results
            })
        }
    },
}
</script>

<template>
    <div class="container">
        <div class="row">
            <div class="col-12">
                <h4>Project types:</h4>
                <div @click="getProjects()">
                    <router-link :to="{ name: 'projects_type', params:{ slug: project_type.slug }}" class="mx-3" v-for="project_type in types">{{ project_type.name }}</router-link>
                </div>
            </div>

            <Project v-for="project in projects" :project="project" />

        </div>
    </div>
</template>

<style scoped lang="scss">
@use '../styles/generals.scss' as *;

.page_button_container {
    display: flex;
    justify-content: center;

    button {
        margin: 5px;
    }

}
</style>