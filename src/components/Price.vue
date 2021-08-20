<template>
    <div>
        <h3>Цена</h3>
        <input type="text" v-model="min" class="priseDisplay"> -
        <input type="text" v-model="max" class="priseDisplay">

        <DoubleRangeSlider :min-range="0" :max-range="100500" @input="changeRange"></DoubleRangeSlider>

    </div>
</template>

<script>
    import DoubleRangeSlider from './doubleRange/DoubleRangeSlider';

  export default {
    name: "Price",
    data () {
      return {
        min: null,
        max: null
      }
    },
    methods: {
      changeRange(range) {
        [this.min, this.max] = [...range];
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
