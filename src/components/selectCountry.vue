<template>
   <select v-model="this.selected" @change="onChange()" class="form-select block w-full border mt-10 p-3 rounded mb-10 focus:outline-none">
       <option value="0">select country</option>
       <option v-for="country in countries" :key="country.ID" :value="country.ID">{{ country.Country }}</option>
   </select>
</template>

<script>
export default {
    name: "selectCountry",
    props: ['countries'],

    data() {
        return {
            selected: 0,
        }
    },
    methods: {
        onChange() {
            const country = this.countries.find(item => item.ID === this.selected)
            this.$emit('getCountry', country)
        }
    }
}
</script>

<style>

</style>