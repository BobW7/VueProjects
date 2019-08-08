<template>
  <div>
    广告发布:{{ getTotalPrice }}
  </div>
</template>

<script>
  export default{
    name:"hill",
    data(){
      return{

      }
    },
    computed: {
      getTotalPrice() {
        return this.$store.getters.getTotalPrice;
      }
    },
  }
</script>

<style scoped>
</style>
