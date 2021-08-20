<template>
    <div>
        <h3>Цена</h3>
        <input type="text" v-model="min" class="priseDisplay"> -
        <input type="text" v-model="max" class="priseDisplay">

        <DoubleRangeSlider :min-range="0" :max-range="100500" :minPoint="+min" :maxPoint="+max" @input="changeRange"></DoubleRangeSlider>

    </div>
</template>

<script>
    import DoubleRangeSlider from '../doubleRange/DoubleRangeSlider';

  export default {
    name: "Price",
    data () {
      return {
        min: 0,
        max: 10050,
      }
    },
    methods: {
      changeRange(range) {
        [this.min, this.max] = [...range];
        this.$emit('changePriceRange', {min: this.min, max:this.max});
      }
    },
    watch: {
      min(val) {
        if(this.max - val < 0) {
          this.max = val;
        }
      },
      max(val) {
        if(this.min - val > 0) {
          this.min = val;
        }
      }
    },
    components: {
      DoubleRangeSlider
    }
  }
</script>

<style scoped>
.priseDisplay {
    border: 1px solid #EAEAEA;
    border-radius: 8px;
    padding: 14px;
}
</style>
