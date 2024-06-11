<template>
    <div v-if="project">
        <h1>{{ project.title }}</h1>
        <p>{{ project.content }}</p>
        <span>{{ project.type?.name }}</span>
        <router-link :to="{name: 'single-project', params: {'slug': 'recusandae-soluta-dolor-et'}}">Leggi altro articolo</router-link>
    </div>
</template>

<script>
import {store} from '../store';
import axios from 'axios';
    export default {
        name: 'ProjectComponent',
        data(){
            return{
                store,
                project: null
            }
        },
        methods: {
            getProject(){
                console.log(this.$route);
                axios.get(`${this.store.apiBaseUrl}/projects/${this.$route.params.slug}`).then((res) => {
                    console.log(res.data);
                    this.project = res.data.results;
                }).catch((error) =>{
                    //console.log(error);
                    //console.log(error.response.data);
                    this.$router.push({name: 'not-found'});
                }).finally();
            }
        },
        mounted(){
            this.getProject();
        },
        created(){
            this.$watch(
                () => this.$route.params,
                (toParams, previousParams) => {
                    this.getProject();
                }
            );
        }
    }
</script>

<style lang="scss" scoped>

</style>