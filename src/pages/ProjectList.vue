<template>
    <h1>All Projects</h1>
    <div class="row">
        <div class="col-12 col-lg-6" v-for="project in projects" :key="project.id">
            <CardComponent :item="project"/>
        </div>
    </div>
</template>

<script>
import { store } from '../store';
import axios from 'axios';
import CardComponent from '../components/CardComponent.vue';
export default {
    name: 'ProjectList',
    components: {
        CardComponent
    },
    data() {
        return {
            store,
            projects: []
        }
    },
    methods: {
        getAllProjects() {
            axios.get(this.store.apiBaseUrl + '/projects').then((res) => {
                console.log(res.data);
                this.projects = res.data.results;
            });
        }
    },
    mounted() {
        this.getAllProjects();
    }
}
</script>

<style lang="scss" scoped></style>