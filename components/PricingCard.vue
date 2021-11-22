<template> 
  <b-card
    :border-variant="isHovered ? 'primary' : 'grey'"
    :header="name"
    :header-bg-variant="isHovered ? 'primary' : 'light'"
    :header-text-variant="isHovered ? 'white' : 'dark'"
    header-class="header-title"
    align="center"
    v-b-hover="hoverHandler" 
    class="mx-20 my-20"     
  >         
    <b-card-text>
      <h4>{{ formatPrice }}</h4>
      <ul>
        <li v-for="feature in features" :key="feature" class="list-unstyled">
          {{ feature }}
        </li>
      </ul>
    </b-card-text>
    <b-button @click="selectPlan(name)" :variant="name === 'Free' ? 'outline-primary' : 'primary'">{{ cta }}</b-button>
  </b-card> 
</template>

<script>
export default {
  name: 'PricingCard',
  props: [
      'name',
      'cost',
      'features',
      'cta',
      'paid'
  ],
  data () {
    return{
      isHovered: false
    }
  },
  computed: {
    formatPrice(){
      return "$" + this.cost + "/mo"
    }
  },
  methods: {
    hoverHandler(hovered) {
        this.isHovered = hovered
    },
    selectPlan(name) {
      const selectedPlan = {
        name: this.name,
        cost: this.cost,
        features: this.features,
        cta: this.cta,
        paid: this.paid
      }
      this.$store.commit('setPlan', selectedPlan)
    }        
  }
};
</script>
<style scoped>
.header-title{
  font-size: 1.75em;  
}
</style>