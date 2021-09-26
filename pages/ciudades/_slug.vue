<script>
  export default {
    async asyncData({ $content, params }) {
      const ciudad = await $content('ciudades', params.slug).fetch()
      const edificios = await $content('edificios').where({ ciudadId: params.slug }).fetch()
      return { ciudad, edificios }
    }
  }
</script>

<template>
  <div class="container">
   <HeaderView />
   <div class="row">
     <div class="three columns">
       <img class="u-max-full-width" :src="'/images/'+ciudad.image">
     </div>
     <div class="six columns">
       <h4>{{ciudad.name}}</h4>
	   Country: {{ciudad.country}};<br>
	   <b>History</b><br>
	    <nuxt-content :document="ciudad" />
	 </div>
	 <div class="three columns"></div>
	   <h5>Edificios</h5>
	   <ul>
	     <li v-for="edificio of edificios" :key="edificio.slug">
	       <NuxtLink :to="{ name: 'edificios-slug', params: { slug: edificio.slug } }">{{edificio.title}}</NuxtLink>
	     </li>
	   </ul>
   </div>
   <FooterView />
 </div>
</template>