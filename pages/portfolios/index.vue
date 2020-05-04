<template>
  <div class="container">
      <nuxt-link :to="{ path: '/'}"> udk-ui </nuxt-link> / portfolios
      <p></p>
      <h1> Portfolios </h1>
      <ul>
         <li v-for="(student, index) in students" :key="index">
          <nuxt-link :to="{ name: 'portfolios-username',  params: {username: student.username}}"> {{student.username}} (id: {{student.id}}) </nuxt-link>
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
      students: []
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
