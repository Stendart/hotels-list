<template>
    <div>
        <AppCountry :countryList="country"></AppCountry>
    </div>
</template>

<script>
    import AppCountry from './AppCountry';

  export default {
    name: "AppFilters",
    props: {
      country: {}
    },
    components: {
      AppCountry
    }
  }
</script>

<style scoped>

</style>
