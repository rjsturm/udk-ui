<template>
  <div class="container">
      <nuxt-link :to="{ path: '/'}"> udk-ui  </nuxt-link>  /
      {{this.catname}}
      <br>
      <p></p>
      <h1> {{this.catname}}</h1>
      <ul>
        <li v-for="(project, index) in projects" :key="index" >
             <div v-if="catname == project.categories[0].Name">
            <nuxt-link :to="{ name: 'portfolios-projects-projectname', params: {projectname: project.Name}}"> {{project.Name}}</nuxt-link>
            {{project.Description}}<br>
            </div>
        </li>
      </ul>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  props: ['name'],
  name: 'projects',
  data(){
    return {
      projects: [],
      catname: this.$route.params.catname
    }
  },
  components: {
  },
  mounted(){
    axios.get('http://localhost:1337/projects', { 
      })
        .then(response => {
          this.projects = response.data
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
