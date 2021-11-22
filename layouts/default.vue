<template>
  <b-container>
    <b-row class="my-5">
      <b-col>
        <h1>Company Inc.</h1>
        <NuxtLink to="/">Home</NuxtLink>
        <NuxtLink to="pricing">Pricing</NuxtLink>
      </b-col>
    </b-row>
    <b-row>
      <b-col>
        <Nuxt />
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
export default {
  name: 'Default',
};
</script>

<style lang="scss" scoped>
/* Reduce the h1 font-size on small displays */
h1{  
  @media (max-width: 640px) {
    font-size: 2rem;
  }
}

/* Give the nuxt active menu link a bold font */
.nuxt-link-exact-active  {
  font-weight: bold;
}
</style>
