<template>
    <div>
        <vue-range-slider
                v-model="value"
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
    },
    data() {
      return {
        value: [this.minRange, this.maxRange]
      }
    },
    watch: {
      value(val) {
        this.$emit('input', val)
      }
    },
    components: {
      VueRangeSlider
    }
  }
</script>

<style scoped>
</style>
