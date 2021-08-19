<template>
    <div>
        <h3>Страна</h3>
        <input type="search" placeholder="Поиск стран" class="search" v-model="searchString">

        <form action="" @submit.prevent="setCountry">
            <template v-if="filteredCountry.length">
                <div v-for="country in filteredCountry" :key="country.id">
                    <label>
                        <input type="checkbox"  :name="country.name"
                               :value="country.name" v-model="selectCountryList">
                        {{country.name}}
                    </label>
                </div>
            </template>
            <template v-else>
                <h3>Такой страны нет</h3>
            </template>

            <button>Send</button>
        </form>

        Выбранные страны = {{selectCountryList}}

    </div>
</template>

<script>
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
      setCountry(d) {
        console.log(d)
      }
    },
    computed: {
      getConuntry() {
        const result = Object.keys(this.countryList.country)
          .map((key) => (
            {
              id: Number(key),
              name: this.countryList.country[key]
            }));
        console.log('result', result)
        return result
      },
      filteredCountry() {
        if(!this.searchString) {
          return this.getConuntry;
        }
        return this.getConuntry.filter(country => country.name.toLowerCase().includes(this.searchString.toLowerCase()));
      }
    },
  }
</script>

<style scoped>
    .search {
        border: 1px solid #EAEAEA;
        box-sizing: border-box;
        border-radius: 10px;

        background: url("../assets/search.png") center left     no-repeat;

        padding: 14px 0 14px 25px;
    }
</style>
