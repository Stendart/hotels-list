<template>
    <div>
        <h3>Количество отзывов (от)</h3>
        <input type="text" :value="value" @input="checkNatural">
    </div>
</template>

<script>
  export default {
    name: "ReviewsCount",
    // data() {
    //   return {
    //     count: null
    //   }
    // },
    props: {
      value: {
        default: 0
      }
    },
    methods: {
      isWhole(n) {
        return /^\d+$/.test(n);
      },
      checkNatural(e) {
        if(!this.isWhole(e.target.value)) {
          e.target.value = e.target.value.slice(0, -1);
        }
        this.$emit('input', e.target.value)
      }
    },

  }
</script>

<style scoped>

</style>
