<script >
export default {
    data() {
        return {
            navLinks: [
                {
                    name: 'home',
                    label: 'Home',
                },
                {
                    name: 'projects',
                    label: 'Projects',
                },
            ],

        };
    },
    created() {

    },
    methods: {

    },
}
</script>

<template>
  <header>
    <div class="container mb-5">
        <div class="row">
            <div class="col-6">
                <h1>BoolFolio</h1>
            </div>
            <div class="col-6 d-flex align-items-center">
                x x 
                <ul class="list-unstyled d-flex mb-0">
                    <li class=" mx-2" v-for="link, index in navLinks">
                        <router-link :to="{ name: link.name }">{{ link.label }}</router-link>
                    </li>
                </ul>
            </div>
        </div>
    </div>
  </header>
</template>


<style scoped lang="scss">

</style>