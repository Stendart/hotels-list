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
import AppCountry from './filters/AppCountry';
import AppType from './filters/AppType';
import AppStars from './filters/AppStars';
import ReviewsCount from './filters/ReviewsCount';
import Price from './filters/Price';

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
      applyFilters() {
        this.$emit('applyFilters', this.collectParams);
      },
      resetFilteres() {
        this.selectCountryList = ['Греция'];
        this.selectTypeList = ['Отель'];
        this.selectStars = ['4 звезды'];
        this.reviewsCount = 0;
        this.priceRange = [0, 100500];

        this.$emit('applyFilters', this.collectParams);
      }
    },
    computed: {
      collectParams() {
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
        return filtersParams
      }
    },
    mounted() {
      this.resetFilteres();
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
    background: #64cb5e;
    color: #fff;
    border-color: #64cb5e;
}
.btn-clear {
    background: #fff;
    border-color: #EAEAEA;
}
</style>
