<template>
  <div>
    <b-container class="text-center">
      <b-row>
        <b-col class="mt-5">
          <h1>Pricing</h1>
        </b-col>
      </b-row>
      <b-row class="justify-content-center">
        <b-col>
          <p class="pb-4">
            Lorem ipsum dolor sit amet consectetur, adipisicing elit. Explicabo,
            tenetur. Eius, fugit quidem tempore, quia officia impedit possimus
            officiis doloremque autem illum reiciendis libero dignissimos
            repellendus dolores veniam error odit!
          </p>
        </b-col>
      </b-row>
      <b-row class="justify-content-center">
        <b-col>
          <b-card-group deck>
            <PricingCard 
              v-for="price in getPriceList"
              :key="price.name"
              :name="price.name"
              :cost="price.cost"
              :features="price.features"
              :cta="price.cta"
              :paid="price.paid"            
            />
          </b-card-group>
        </b-col>
      </b-row>
    </b-container>
    <b-modal ref="the-modal" title="New Plan Selected">
      <p class="my-4">You have chosen: <strong>{{ selectedPlanName }}</strong></p>
    </b-modal>
  </div>
</template>

<script>
import PricingCard from '../components/PricingCard.vue';

export default {
  name: 'Pricing',
  layout: 'default',
  components: {
    PricingCard
  },
  data () {
    return {
      selectedPlanName: ''
    }
  },
  computed: {        
    getPriceList(){
      return this.$store.state.pricingOptions
    },
     getSelectedPlan(){
      return this.$store.state.chosenPlan
    }
  },
  methods: {
    hoverHandler(hovered) {
        this.isHovered = hovered
    }
  },
  watch: {
    // Check if the selectedPlan data in state has updated from the default of null,
    // Then show the modal with the name of the Selected Plan
    getSelectedPlan() {
      if(this != null){
        this.selectedPlanName = this.getSelectedPlan.name;
        this.$refs['the-modal'].show()      
      }
    }
  }
};
</script>

<style lang="scss" scoped>
p {
  color: #6c757d;
  font-size: 1.25rem;
}
</style>
