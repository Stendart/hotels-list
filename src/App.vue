<template>
  <div id="app">
    <main class="main">
      <AppFilters :country="countryList" class="filter-wrapper"
                  @changeCountryList="setCountryList"
                  @changeType="setTypes"
                  @changeStars="setStars"
                  @changeReviewsCount="setReviewsCount"
                  @changePriceRange="setPriceRange"

                  @applyFilters="applyFilters"></AppFilters>
      <HotelsList :hotels="hotelsList" class="hotel-wrapper"></HotelsList>
    </main>
  </div>
</template>

<script>
import hotels from "./assets/hotels.json";
import country from "./assets/country.json";

import AppFilters from './components/filters/AppFilters';
import HotelsList from './components/HotelsList';

export default {
  name: 'App',
  data() {
    return {
      selectCountryList: [],
      selectTypeList: [],
      selectStars: [],
      reviewsCount: 0,
      priceRange: {},
    }
  },
  // created() {
  //   console.log('test', hotels)
  //   console.log('country', country)
  // },
  methods: {
    setCountryList(list) {
      this.selectCountryList = list;
    },
    setTypes(list) {
      this.selectTypeList = list;
    },
    setStars(list) {
      this.selectStars = list;
    },
    setReviewsCount(count) {
      this.reviewsCount = count;
    },
    setPriceRange(range) {
      this.priceRange = range;
    },

    applyFilters(filtersParams) {
      console.log('filtersParams', filtersParams)
      // console.log('selectStars', parseInt(filtersParams.selectStars[0]))
      console.log('hotelsList', this.hotelsList)

      const filteredByCountry = this.filteredByParam(this.hotelsList, 'country', filtersParams.selectCountryList);
      const filteredByType = this.filteredByParam(filteredByCountry, 'type', filtersParams.selectTypeList);
      const filteredByStars = this.filteredByParam(filteredByType, 'stars', filtersParams.selectStars);

      const filteredByReviews = this.filteredByCompaire(filteredByStars, 'reviews_amount', filtersParams.reviewsCount)
      const filteredByPrice = this.filteredByCompaire(filteredByReviews, 'min_price', filtersParams.priceRange.min, filtersParams.priceRange.max)
      console.log('filteredByStars', filteredByPrice)
    },

    filteredByParam(arr, fieldName, param) {
      return arr.filter(el => {
        return param.includes(el[fieldName])
      })
    },
    filteredByCompaire(arr, fieldName, param1, param2) {
      if(!param2) {
        return arr.filter(el => {
          return el[fieldName] > param1
        })
      } else {
        return arr.filter(el => {
          return el[fieldName] > param1 && el[fieldName] < param2
        })
      }

    }
  },
  computed: {
    countryList() {
      return country;
    },
    hotelsList() {
      return hotels.hotels;
    }
  },
  components: {
    AppFilters,
    HotelsList
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /*text-align: center;*/
  color: #2c3e50;
  margin-top: 60px;


}

  .main {
    display: flex;
    justify-content: space-between;

    width: 90%;
    margin: 0 auto;
  }

  .filter-wrapper {
    width: 30%;
  }
  .hotel-wrapper {
    width: 65%;
  }
</style>
