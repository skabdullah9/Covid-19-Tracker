<template>
  <div class="text-center mb-10">
      <h2 class="font-bold text-3xl text-gray-700 mb-3">{{title}}</h2>
      <h2>{{timestamp}}</h2>
  </div>
</template>

<script>
import moment from 'moment'
export default {
    name: "dataTitle",
    props: ['title', 'date'],
    computed: {
        timestamp: function() {
            return moment(this.date).format('MMMM Do YYYY, hh:mm:ss a')
        }
    }
}
</script>

<style>

</style>