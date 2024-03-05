<script >
import axios from 'axios';
import { store } from '../store.js';
export default {
    
    data() {
        return {
            store,
            project: null,
        }
    },
    created() {
        this.getProject();
    },
    methods: {
         getProject(slug) {
              axios.get(`${this.store.endpoint}/api/projects/${this.$route.params.slug}`,).then((response) => {
                  this.project = response.data.project;
              });
         },
         getImage() {
            let image;

            if (this.project.img != null) {

                if (this.project.img.includes('https')) {

                    return `${this.project.img}`

                } else {
                    image = `/storage/${this.project.img} `
                }

            } else {
                image = '/storage/project_images/placeholder.png'
            }

            return `${this.store.endpoint}${image}`
        },
          
    },
}
</script>

<template>
    <div class="container">
        <div class="row">
            <div class="card" style="width: 30rem;">
                <img class="card-img-top " :src="getImage()" :alt="project.name">
                <div class="card-body">
                    <h5 class="card-title">Project name:{{ project.name }}</h5>
                    <p class="card-text">Project description:  {{ project.description }}</p>
                    <p class="card-text">Project slug:  {{ project.slug}}</p>
                    <p class="card-text">Project repository link:  {{ project.repository_link}}</p>
                    <p class="card-text">Project starting date:  {{ project.date_start }}</p>
                    <p class="card-text">Project ending date:  {{ project.date_end }}</p>
                    <p class="card-text">Project type:  {{ project.type ? project.type.name : 'Nessuna tipologia specificata' }} </p>
                </div>
            </div>

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