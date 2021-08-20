<template>
    <div>
        <AppCountry :countryList="country"></AppCountry>
        <AppType :type-list="typeList"></AppType>
        <AppStars></AppStars>
        <ReviewsCount></ReviewsCount>
        <Price></Price>

        <button>Применить фильтр</button>
        <button>Очистить фильтр</button>
    </div>
</template>

<script>
    import AppCountry from './AppCountry';
    import AppType from './AppType';
    import AppStars from './AppStars';
    import ReviewsCount from './ReviewsCount';
    import Price from './Price';

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
      ReviewsCount,
      Price
    }
  }
</script>

<style scoped>

</style>
