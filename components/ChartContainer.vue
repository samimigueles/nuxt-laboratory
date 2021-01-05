<template>
  <div class="container">
    <Chart
      v-if="loaded"
      :chartdata="chartdata"
      :options="options"/>
  </div>
</template>

<script>
import Chart from './Chart.vue'

export default {
  name: 'LineChartContainer',
  components: { Chart },
  data: () => ({
    loaded: false,
    chartdata: null
  }),
  async mounted () {
    this.loaded = false
    try {
      const { userlist } = await fetch('https://jsonplaceholder.typicode.com/users')
      this.chartdata = userlist
      this.loaded = true
    } catch (e) {
      console.error(e)
    }
  }
}
</script>