<template>
  <h1 class="text-center">Ciao</h1>
  <i class="fa fa-solid fa-home"></i>
  
  <ul>
    <li v-for="(item, index) in menuItems" :key="index">
      <router-link :to="{name: item.routeName}" class="nav-link">
        {{ item.label }}
      </router-link>
    </li>
  </ul>

  <main class="container">
    <router-view></router-view>
  </main>
</template>

<script>
import {store} from './store';
import axios from 'axios';
  export default {
    name: 'App',
    data(){
      return{
        menuItems: [
          {
            label: 'Home',
            routeName: 'home'
          },
          {
            label: 'Projects',
            routeName: 'projects'
          },
          {
            label: 'Type',
            routeName: 'types'
          }
        ]
      }
    }
    
  }
</script>

<style lang="scss" scoped>

</style>