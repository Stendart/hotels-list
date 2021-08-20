<template>
    <div>
        <div v-for="item in listItem" :key="item.id">
            <label>
                <input type="checkbox"  :name="item.title"
                       :value="item.title" v-model="check" >
                {{item.title}}
            </label>
        </div>
    </div>
</template>

<script>
  export default {
    name: "CheckboxGroup",
    props: {
      // value: {},
      listItem: {}
    },
    data() {
      return {
        // content: this.value,
        check: []
      }
    },
    methods: {
      // handleInput (e) {
      //   this.$emit('input', e.target.value)
      // }
    },
    watch: {
      check(newVal) {
        this.$emit('input', newVal);
      }
    }
  }
</script>

<style scoped>

</style>
