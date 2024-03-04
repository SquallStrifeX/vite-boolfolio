<script >
import { store } from '../store.js';
export default {
    props: {
        project: Object
    },
    data() {
        return {
            store,
        }
    },
    created() {

    },
    methods: {
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

            return `${this.store.endpoint}${image} `
        }
    },
}
</script>

<template>
    <div class="col-2 m-5">
        <div class="card" style="width: 15rem;">
            <img class="card-img-top " :src="getImage()" :alt="project.name">
            <div class="card-body">
                <h5 class="card-title">{{ project.name }}</h5>
                <p class="card-text">{{ project.description }}</p>
                <p class="card-text">{{ project.type ? project.type.name : 'Nessuna tipologia specificata' }} </p>
                <a href="#" class="btn btn-primary">Vai al dettaglio</a>
            </div>
        </div>
    </div>
</template>

<style scoped lang="scss">

</style>