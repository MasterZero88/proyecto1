<script>
  export default {
    async asyncData({ $content, params }) {
      const edificio = await $content('edificios', params.slug).fetch()
      const arquitecto = await $content('arquitectos').where({ id: edificio.arquitectoId }).only(['name']).fetch()
      const ciudad = await $content('ciudades').where({ id: edificio.ciudadId }).only(['name']).fetch()
      return { edificio, arquitecto, ciudad }
    }
  }
</script>

<template>
  <div class="container">
   <HeaderView />
   <div class="row">
     <div class="three columns">
       <img class="u-max-full-width" :src="'/images/'+edificio.image" alt="Italian Trulli">
     </div>
     <div class="six columns">
       <h4>{{edificio.title}}</h4>
	   by <NuxtLink :to="'/authors/'+edificio.arquitectoId">{{arquitecto[0].name}}</NuxtLink><br>
       
	   <b>Description</b><br>
	    <nuxt-content :document="book" />
	 </div>
	 <div class="two columns"></div>
   </div>
   <FooterView />
 </div>
</template>