<template>
    <div>
        <h3>Страна</h3>
        <input type="search" placeholder="Поиск стран" class="search" v-model="searchString">

        <form action="" @submit.prevent="" class="country-wrapper">
            <template v-if="filteredCountry.length">
                <CheckboxGroup :list-item="filteredCountry" :default-val="value" @input="setSelectCountry"></CheckboxGroup>
            </template>
            <template v-else>
                <h3>Такой страны нет</h3>
            </template>
        </form>
    </div>
</template>

<script>
import CheckboxGroup from './CheckboxGroup';

  export default {
    name: "AppCountry",
    props: {
      countryList: {},
      value: {}
    },
    data() {
      return {
        searchString: '',
        selectCountryList: ['Алжир']
      }
    },
    methods: {
      setSelectCountry(countryList) {
        this.selectCountryList = countryList;
        this.$emit('changeCountryList', this.selectCountryList);
        this.$emit('input', countryList);
      }
    },
    computed: {
      getConuntry() {
        const result = Object.keys(this.countryList.country)
          .map((key) => (
            {
              id: Number(key),
              title: this.countryList.country[key]
            }));
        return result;
      },
      filteredCountry() {
        if(!this.searchString) {
          return this.getConuntry;
        }
        return this.getConuntry.filter(country => country.title.toLowerCase().includes(this.searchString.toLowerCase()));
      }
    },
    components: {
      CheckboxGroup
    }
  }
</script>

<style scoped>
    .search {
        border: 1px solid #EAEAEA;
        box-sizing: border-box;
        border-radius: 10px;

        background: url("../../assets/search.png") center left     no-repeat;

        padding: 14px 0 14px 25px;
    }

    .country-wrapper {
        border: 1px solid #EAEAEA;
        box-sizing: border-box;
        border-radius: 10px;

        max-height: 20vh;

        overflow-y: auto;
    }
</style>
