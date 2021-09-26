<script>
  export default {
    async asyncData({ $content, params }) {
      const edificios = await $content('edificios').fetch()
      return {
        edificios
      }
    }
  }
</script>

<template>
  <div class="container">
   <HeaderView />
   <h3 style="margin-top: 15px">Buildings Information</h3>
     <p>This section presents information about buildings</p>
   <ul>
     <li v-for="edificio of edificios" :key="edificio.slug">
       <NuxtLink :to="{ name: 'edificios-slug', params: { slug: edificio.slug } }">{{edificio.title}}</NuxtLink>
     </li>
   </ul>
   <FooterView />
 </div>
</template>