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
      listItem: {},
      defaultVal: {
        default: () => []
      }
    },
    data() {
      return {
        check: this.defaultVal
      }
    },
    watch: {
      check(newVal) {
        this.$emit('input', newVal);
      },
      defaultVal(newVal) {
        this.check = newVal;
      }
    }
  }
</script>

<style scoped>

</style>
