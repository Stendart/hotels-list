<template>
    <div>
        <h3>Звезды</h3>
        <CheckboxGroup :list-item="transformStars" :default-val="value" @input="setStars"></CheckboxGroup>
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
      },
      value: {}
    },
    data() {
      return {
        stars: this.value
      }
    },
    methods: {
      setStars(stars) {
        this.stars = stars;
        // console.log(stars)
        // this.$emit('changeStars', this.stars);
        this.$emit('input', stars);
      },
    },
    watch: {
      value(newVal) {
        this.stars = newVal;
      }
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
