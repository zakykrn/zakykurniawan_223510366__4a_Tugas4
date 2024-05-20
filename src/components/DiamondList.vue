<template>
    <div class="diamond-container">
      <DiamondItem 
        v-for="diamond in diamonds" 
        :key="diamond.id" 
        :diamond="diamond" 
        @diamondSelected="handleDiamondSelected" />
    </div>
  </template>
  
  <script>
  import DiamondItem from './DiamondItem.vue';
  
  export default {
    components: {
      DiamondItem
    },
    props: {
      diamonds: {
        type: Array,
        required: true
      }
    },
    methods: {
      handleDiamondSelected(diamond) {
        this.$emit('diamondSelected', diamond);
      }
    }
  }
  </script>
  