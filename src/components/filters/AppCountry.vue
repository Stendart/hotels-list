<template>
    <div>
        <h3>Страна</h3>
        <input type="search" placeholder="Поиск стран" class="search" v-model="searchString">

        <form action="" @submit.prevent="" class="country-wrapper">
            <template v-if="filteredCountry.length">
                <CheckboxGroup :list-item="filteredCountry" @input="setSelectCountry"></CheckboxGroup>
<!--                <div v-for="country in filteredCountry" :key="country.id">-->
<!--                    <label>-->
<!--                        <input type="checkbox"  :name="country.name"-->
<!--                               :value="country.name" v-model="selectCountryList">-->
<!--                        {{country.name}}-->
<!--                    </label>-->
<!--                </div>-->
            </template>
            <template v-else>
                <h3>Такой страны нет</h3>
            </template>

        </form>

        Выбранные страны = {{selectCountryList}}

    </div>
</template>

<script>
    import CheckboxGroup from './CheckboxGroup';

  export default {
    name: "AppCountry",
    props: {
      countryList: {}
    },
    data() {
      return {
        searchString: '',
        selectCountryList: []
      }
    },
    methods: {
      setSelectCountry(countryList) {
        this.selectCountryList = countryList
        console.log(this.selectCountryList)
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
        console.log('result', result)
        return result
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
