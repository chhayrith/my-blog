<template>
  <div>
    <b-table striped hover :items="items" :fields="fields"></b-table>
  </div>
</template>

<script>
import tButtonVue from '../button-table/t-button.vue';
  export default {
    components:{
      tButtonVue
    },
    data() {
      return {
        // Note `isActive` is left out and will not appear in the rendered table
        fields: ['first_name', 'last_name', 'age'],
        items: [
          { isActive: true, age: 40, first_name: 'Dickerson', last_name: 'Macdonald' },
        ]
      }
    },
    methods: {
      add(item) {
        this.items.push(item)
      }
    }
  }
</script>

<style>

</style>
