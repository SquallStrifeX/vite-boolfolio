<script >
import axios from 'axios';
import { store } from '../store.js';
import Project from './Project.vue';

export default {
    components: {
        Project,
    },
    data() {
        return {
            store,
            projects: [],
        }
    },
    created() {
        this.getProjects();
    },
    methods: {
        getProjects() {
            axios.get(`${this.store.endpoint}/api/projects`).then((response) => {
                console.log(response.data.results);
                this.projects = response.data.results;
                console.log(this.projects);
            })
        }
    },
}
</script>

<template>
    <div class="container">
        <div class="row">
            kkkk
            <Project v-for="project in projects" :key="index" :project="project" />
        </div>
    </div>
</template>

<style scoped lang="scss">

</style>