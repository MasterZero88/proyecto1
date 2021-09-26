<script>
  export default {
    async asyncData({ $content, params }) {
      const ciudades = await $content('ciudades').fetch()
      return {
        ciudades
      }
    }
  }
</script>

<template>
  <div class="container">
   <HeaderView />
   <h3 style="margin-top: 15px">Cities Information</h3>
     <p>This section presents information about cities</p>
   <ul>
     <li v-for="ciudad of ciudades" :key="ciudad.slug">
       <NuxtLink :to="{ name: 'ciudades-slug', params: { slug: ciudad.slug } }">{{ciudad.name}}</NuxtLink>
     </li>
   </ul>
   <FooterView />
 </div>
</template>