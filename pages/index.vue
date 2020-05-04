<template>
  <div class="container">
      udk-ui <br>
          <p></p>
          <div>
          <nuxt-link :to="{ name: 'portfolios'}"> portfolios </nuxt-link> <br>
          <nuxt-link :to="{ name: 'categories'}"> categories </nuxt-link> <br>
          <nuxt-link :to="{ name: 'projects'}"> all Projcts  </nuxt-link> <br>
          <nuxt-link :to="{ name: 'docu'}"> Documentation </nuxt-link> <br>
          </div>
     <br>
     <div class="news">
      <h1>News</h1>
      <P></P>
       <ul class="reverse"> <!-- Reverse order by css -->
         <li v-for="(post, index) in posts" :key="index">
          <h3>  {{post.Headline}} </h3>
           <div v-if="post.image[0] === undefined">
           </div>
           <div v-else>  
           <img :src="'http://localhost:1337' + post.image[0].formats.small.url">
           </div>
          <div v-html="$md.render(post.maincontent)"></div>  <!-- Markdown OUTPUT !! -->
          <p></p>
      </li>
      </ul>
      </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'app',
  data(){
    return {
      posts: []
    }
  },
  components: {

  },
  mounted(){
    axios.get('http://localhost:1337/newsposts', { // http://odp-lic.ppe-aws.europeandataportal.eu:9090/data/ds-per-catalogue'
      })
        .then(response => {
          this.posts = response.data
        })
  }
}
</script>

<style scoped>
.news li { list-style-type: none;}

.reverse {
  display: flex;
  flex-direction: column-reverse;
}

ul { 
padding-inline-start: 0px !important;
padding-left: 0px; }
</style>
