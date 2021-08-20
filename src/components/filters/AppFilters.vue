<template>
    <div>
        <AppCountry :countryList="country" v-model="selectCountryList"></AppCountry>
        <AppType :type-list="typeList" v-model="selectTypeList"></AppType>
        <AppStars v-model="selectStars"></AppStars>

        <ReviewsCount v-model="reviewsCount"></ReviewsCount>
        <Price v-model="priceRange"></Price>

        <button class="btn btn-primary" @click="applyFilters">Применить фильтр</button>
        <button class="btn btn-clear" @click="resetFilteres">Очистить фильтр</button>
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
        reviewsCount: 0,
        priceRange: [0, 100500],
      }
    },
    methods: {
      /*changeCountryList(countryList) {
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
*/



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
      },
      resetFilteres() {
        this.selectCountryList = [];
        this.selectTypeList = [];
        this.selectStars = [];
        this.reviewsCount = 0;
        this.priceRange = [0, 100500]
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
