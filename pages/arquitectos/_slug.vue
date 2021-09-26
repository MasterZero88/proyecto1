<script>
  export default {
    async asyncData({ $content, params }) {
      const arquitecto = await $content('arquitectos', params.slug).fetch()
      const edificios = await $content('edificios').where({ arquitectoId: params.slug }).fetch()
      return { arquitecto, edificio }
    }
  }
</script>

<template>
  <div class="container">
   <HeaderView />
   <div class="row">
     <div class="three columns">
       <img class="u-max-full-width" :src="'/images/'+arquitecto.image" alt="Italian Trulli">
     </div>
     <div class="six columns">
       <h4>{{arquitecto.name}}</h4>
	   Nationality: {{arquitecto.nationality}}; Born: {{arquitecto.birth_year}}<br>
	   <b>Biography</b><br>
	    <nuxt-content :document="author" />
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