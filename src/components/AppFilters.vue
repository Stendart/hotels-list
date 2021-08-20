<template>
    <div>
        <AppCountry :countryList="country"></AppCountry>
        <AppType :type-list="typeList"></AppType>
        <AppStars></AppStars>
        <ReviewsCount></ReviewsCount>
    </div>
</template>

<script>
    import AppCountry from './AppCountry';
    import AppType from './AppType';
    import AppStars from './AppStars';
    import ReviewsCount from './ReviewsCount';

  export default {
    name: "AppFilters",
    props: {
      country: {}
    },
    data() {
      return {
        typeList: [
          {
            id:1,
            title: 'Апартаменты'
          },
          {
            id:2,
            title: 'Отель'
          },
        ],
      }
    },
    components: {
      AppCountry,
      AppType,
      AppStars,
      ReviewsCount
    }
  }
</script>

<style scoped>

</style>
