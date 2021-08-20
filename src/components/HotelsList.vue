<template>
    <div>
        <HotelCard v-for="hotel in hotels" :hotel="hotel"></HotelCard>
    </div>
</template>

<script>
    import HotelCard from './HotelCard';
  export default {
    name: "HotelsList",
    props: {
      hotels: {}
    },
    created() {
      console.log('hotels = ', this.hotels)
    },
    components: {
      HotelCard
    }
  }
</script>

<style scoped>

</style>
