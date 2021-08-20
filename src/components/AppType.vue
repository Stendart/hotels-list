<template>
    <div>
        <h3>Тип</h3>
        <CheckboxGroup :list-item="typeList" @input="setType"></CheckboxGroup>
    </div>
</template>

<script>
import CheckboxGroup from './CheckboxGroup';

  export default {
    name: "AppType",
    props: {
      typeList: {}
    },
    data() {
      return {
        types: '',
      }
    },
    methods: {
      setType(type) {
        this.types = type;
        console.log('types = ', this.types);
      }
    },
    components: {
      CheckboxGroup
    }
  }
</script>

<style scoped>

</style>
