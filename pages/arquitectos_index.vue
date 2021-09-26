<script>
  export default {
    async asyncData({ $content, params }) {
      const arquitectos = await $content('arquitectos').fetch()
      return {
        arquitectos
      }
    }
  }
</script>

<template>
  <div class="container">
   <HeaderView />
   <h3 style="margin-top: 15px">Architect Information</h3>
     <p>This section presents information about architects</p>
   <ul>
     <li v-for="arquitecto of arquitectos" :key="arquitecto.slug">
       <NuxtLink :to="{ name: 'arquitectos-slug', params: { slug: arquitecto.slug } }">{{arquitecto.name}}</NuxtLink>
     </li>
   </ul>
   <FooterView />
 </div>
</template>