<template>
    <ul>
        <li v-for="project in projects" :key="project.id">{{ project.title }}
            <div>{{ project.type?.name }}</div>
            <router-link :to="{name: 'single-project', params: {'slug': project.slug}}">Leggi articolo</router-link>
        </li>
    </ul>
</template>

<script>
import { store } from '../store';
import axios from 'axios';
export default {
    name: 'ProjectList',
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