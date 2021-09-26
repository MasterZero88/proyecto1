<template>
 <div class="container">
   <HeaderView />
   <h2 style="margin-top: 15px">Computer Science Books</h2>
	  <p>This website offers information about highest buildings.</p>
    <ul>
	  <li> <NuxtLink to="/edificios_index">Buildings information</NuxtLink></li>
	  <li> <NuxtLink to="/arquitectos_index">Architects information</NuxtLink></li>
	  <li> <NuxtLink to="/ciudades_index">Cities information</NuxtLink></li>
	</ul>
   <FooterView />
 </div>
</template>

<script>
export default {
  head() {
    return {
      script: [{ src: 'https://identity.netlify.com/v1/netlify-identity-widget.js' }],
    };
  },
};
</script>