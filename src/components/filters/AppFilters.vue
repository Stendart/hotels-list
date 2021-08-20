<template>
    <div>
        <AppCountry :countryList="country" @changeCountryList="changeCountryList"></AppCountry>
        <AppType :type-list="typeList" @changeType="changeType"></AppType>
        <AppStars @changeStars="changeStars"></AppStars>
        <ReviewsCount @input="changeReviewsCount"></ReviewsCount>
        <Price @changePriceRange="changePriceRange"></Price>

        <button class="btn btn-primary" @click="applyFilters">Применить фильтр</button>
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

        selectCountryList: [],
        selectTypeList: [],
        selectStars: [],
        reviewsCount: null,
        priceRange: {},
      }
    },
    methods: {
      changeCountryList(countryList) {
        // this.$emit('changeCountryList', countryList);
        this.selectCountryList = countryList;
      },
      changeType(type) {
        // this.$emit('changeType', type);
        this.selectTypeList = type;
      },
      changeStars(stars) {
        // this.$emit('changeStars', stars);
        this.selectStars = stars;
      },
      changeReviewsCount(reviewsCount) {
        // this.$emit('changeReviewsCount', reviewsCount);
        this.reviewsCount = reviewsCount;
      },
      changePriceRange(priceRange) {
        // this.$emit('changePriceRange', priceRange);
        this.priceRange = priceRange;
      },




      applyFilters() {

        const arr = this.selectStars.reduce((acc, el) => {
          acc.push(parseInt(el))
          return acc
        },[])

        const filtersParams = {
          selectCountryList: this.selectCountryList,
          selectTypeList: this.selectTypeList,
          selectStars: arr,
          reviewsCount: this.reviewsCount,
          priceRange: this.priceRange,
        }
        this.$emit('applyFilters', filtersParams);
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
