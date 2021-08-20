<template>
    <div>
        <h3>Количество отзывов (от)</h3>
        <input type="text" class="review" :value="value" @input="checkNatural">
    </div>
</template>

<script>
  export default {
    name: "ReviewsCount",
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
.review {
    border: 1px solid #EAEAEA;
    border-radius: 10px;

    padding: 14px 20px;
}
</style>
