<template>
    <main class="grid md:grid-cols-2 gap-4">
        <div class="bg-indigo-200 rounded text-center shadow-md p-10">
            <h3 class="text-3xl font-bold text-blue-900 mb-3">Cases</h3>
            <div class="text-2xl mb-2">
                <span class="font-bold">New:</span> {{numberWithCommas(stats.NewConfirmed)}}
            </div>
            <div class="text-2xl">
                <span class="font-bold">Total:</span> {{numberWithCommas(stats.TotalConfirmed)}}
            </div>
        </div>
        <div class="bg-indigo-300 rounded text-center shadow-md p-10">
            <h3 class="text-3xl font-bold text-blue-900 mb-3">Deaths</h3>
            <div class="text-2xl mb-2">
                <span class="font-bold">New:</span> {{numberWithCommas(stats.NewDeaths)}}
            </div>
            <div class="text-2xl">
                <span class="font-bold">Total:</span> {{numberWithCommas(stats.TotalDeaths)}}
            </div>
        </div>
        <div class="bg-indigo-100 rounded text-center shadow-md p-10 col-span-2">
            <h3 class="text-3xl font-bold text-blue-900 mb-3">Recovered</h3>
            <div class="text-2xl mb-2">
                <span class="font-bold">New:</span> {{numberWithCommas(stats.NewRecovered)}}
            </div>
            <div class="text-2xl">
                <span class="font-bold">Total:</span> {{numberWithCommas(stats.TotalRecovered)}}
            </div>
        </div>
    </main>
</template>

<script>
export default {
    name: "dataBoxes",
    props: ['stats'],
    methods: {
        numberWithCommas(x) {
            return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',')
        }
    }
}
</script>

<style>

</style>