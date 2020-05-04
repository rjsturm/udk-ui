<template>
  <div class="container">
       <nuxt-link :to="{ path: '/'}"> udk-ui  </nuxt-link> / 
       <nuxt-link :to="{ name: 'portfolios'}"> portfolios  </nuxt-link> / {{username}} 
      <br>
       <p></p>
      <h1> {{username}} </h1>
       <ul>
         <li v-for="(student, index) in students" :key="index">
           <div v-if="username == student.username">
            mail: {{student.email}} <br>
            insta:     <br>
            about me:        <br>
            whatever: ... <br> <p></p>
           <li v-for="(project, index) in student.projects" :key="index">
           <nuxt-link :to="{ name: 'portfolios-projects-projectname', params: {projectname: project.Name, username: student.username}}"><h3> {{project.Name}}  </h3></nuxt-link>
           <p> {{project.Description}}  </p> 
           <div v-if="project.img_small[0] === undefined">
           </div>
           <div v-else>  
           <img :src="'http://localhost:1337' + project.img_small[0].formats.small.url">
           </div>
           <br><p></p>
         </li> 
        </div>
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
      students: [],
      username: this.$route.params.username
    }
  },
  components: {
   },
  mounted(){
    axios.get('http://localhost:1337/users', { // http://odp-lic.ppe-aws.europeandataportal.eu:9090/data/ds-per-catalogue'
      })
        .then(response => {
          this.students = response.data
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
