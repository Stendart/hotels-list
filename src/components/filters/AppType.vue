<template>
    <div>
        <h3>Тип</h3>
        <CheckboxGroup :list-item="typeList" :default-val="value" @input="setType"></CheckboxGroup>
    </div>
</template>

<script>
import CheckboxGroup from './CheckboxGroup';

  export default {
    name: "AppType",
    props: {
      typeList: {},
      value: {}
    },
    data() {
      return {
        types: this.value,
      }
    },
    methods: {
      setType(type) {
        this.types = type;
        console.log('types = ', this.types);
        this.$emit('changeType', this.types);
        this.$emit('input', type);
      }
    },
    watch: {
      value(newVal) {
        this.types = newVal;
      }
    },
    components: {
      CheckboxGroup
    }
  }
</script>

<style scoped>

</style>
