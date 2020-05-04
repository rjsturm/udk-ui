<template>
  <div class="container">
    <div v-for="(project, index) in projects" :key="index">
      <div v-if="projectname == project.Name">
      <nuxt-link :to="{ path: '/'}"> udk-ui  </nuxt-link>  /
      <nuxt-link :to="{ name: 'portfolios'}"> portfolios  </nuxt-link>  / 
      <span v-for="(project, index) in project.users" :key="index">
      <nuxt-link :to="{ name: 'portfolios-username', params: {username: project.username}}"> <span v-if="index >= 1">&</span> {{project.username}} </nuxt-link> 
      </span>
      /
      {{projectname}}
      <br>
      <p></p>
       <h1> {{projectname}} </h1>
       <p> {{project.Description}} </p> 
       <span v-for="(project, index) in project.categories" :key="index">
       <span v-if="index >= 1">&</span> {{project.Name}} 
       </span>
           <div v-if="project.img_small[0] === undefined">
           </div>
           <div v-else>  
           <img :src="'http://localhost:1337' + project.img_small[0].formats.small.url">
           </div>
    </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'projects',
  data(){
    return {
      projects: [],
      projectname: this.$route.params.projectname,
      username: this.$route.params.username
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

</style>
