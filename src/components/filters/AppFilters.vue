<template>
    <div>
        <AppCountry :countryList="country"></AppCountry>
        <AppType :type-list="typeList"></AppType>
        <AppStars></AppStars>
        <ReviewsCount></ReviewsCount>
        <Price></Price>

        <button class="btn btn-primary">Применить фильтр</button>
        <button class="btn btn-clear">Очистить фильтр</button>
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
.btn {
    margin-top: 40px;
    border-radius: 15px;
    padding: 17px 90px;
}
.btn-primary {
    background: #6A53F5;
    color: #fff;
    border-color: #6A53F5;
}
.btn-clear {
    background: #fff;
    border-color: #EAEAEA;
}
</style>
