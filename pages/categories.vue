<template>
  <div class="container">
       <nuxt-link :to="{ path: '/'}"> udk-ui  </nuxt-link> / 
       categories
      <br>
      <p></p>
      <h1> Categories </h1>
      <ul>
         <li v-for="(cat, index) in cats" :key="index">
          <nuxt-link :to="{ name: 'projects-catname' , params: {catname: cat.Name}}"> {{cat.Name}} </nuxt-link>
      </li>
      </ul>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'app',
  data(){
    return {
      cats: []
    }
  },
  components: {
  },
  mounted(){
    axios.get('http://localhost:1337/categories', { 
      })
        .then(response => {
          this.cats = response.data
        })
  }
}
</script>

<style scoped>
li {list-style-type: none;}
ul { 
padding-inline-start: 0px !important;
padding-left: 0px; }

</style>
