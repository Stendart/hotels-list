<template>
    <div>
        <vue-range-slider
                :value="[minPoint, maxPoint]"
                @input="inputHandler"
                :min="minRange"
                :max="maxRange"
                :enable-cross="false"
                :bg-style="{ }"
                :slider-style="{ backgroundColor: '#64cb5e', borderRadius: '50%'}"
                :process-style="{ backgroundColor: '#64cb5e'}"
                :tooltip-style="{backgroundColor: '#64cb5e', borderColor:'#64cb5e'}"
                :tooltip-dir="'bottom'"
                :tooltip-merge="false"

                :dot-size="20"
        ></vue-range-slider>
    </div>
</template>

<script>
  import './vue-range-slider.css'
  import './inputRange.css'
  import VueRangeSlider from './inputRange'
  export default {
    name: "inputRange",
    props: {
      minRange: {
        type: Number,
        default: 0
      },
      maxRange: {
        type: Number,
        default: 100
      },
      minPoint: {
        type: Number,
        default: 0
      },
      maxPoint: {
        type: Number,
        default: 100
      },
    },
    methods: {
      inputHandler(e) {
        this.$emit('input', e)
      }
    },
    components: {
      VueRangeSlider
    }
  }
</script>

<style scoped>
</style>
