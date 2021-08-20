<template>
    <div>
        <h3>Звезды</h3>
        <CheckboxGroup :list-item="transformStars" :default-val="stars" @input="setStars"></CheckboxGroup>
    </div>
</template>

<script>
import {declOfNum} from '../../utils';
import CheckboxGroup from './CheckboxGroup';

  export default {
    name: "AppStars",
    props: {
      countStars: {
        type: Number,
        default: 5
      }
    },
    data() {
      return {
        stars: ['1 звезда', '4 звезды'],
      }
    },
    methods: {
      setStars(stars) {
        this.stars = stars;
        console.log(stars)
        this.$emit('changeStars', this.stars);
      },
      // declOfNum(number, titles) { // проверка окончания существительного после числительного
      //   const cases = [2, 0, 1, 1, 1, 2];
      //   return titles[ (number%100>4 && number%100<20)? 2 : cases[(number%10<5)?number%10:5] ];
      // },
    },
    computed: {
      transformStars() {
        const starList = [];
        for(let i = 0; i < this.countStars; i++) {
          starList.push(
            {
              id: i,
              title: `${i+1} ${declOfNum(i+1, ['звезда', 'звезды', 'звезд'])}`
            });
        }
        return starList
      }
    },
    components: {
      CheckboxGroup
    }
  }
</script>

<style scoped>

</style>
