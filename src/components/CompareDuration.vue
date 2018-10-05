<template>
  <div>
    <highcharts :options="options"></highcharts>
  </div>
</template>

<script>
export default {
  data() {
    return {
      options: {
        series: [{
          name: 'Ипотека',
          data: this.payments()
        }]
      },
    }
  },
  methods: {
    calculateVariant(sum, percent, years) {
      percent = percent / 1200;
      years = years * 12;
      let payment = (sum * percent / (1 - Math.pow(1 + percent, -years)));
      return payment;
    },
    payments() {
      let result = [];
      for (let i = 5; i <= 31; i++) {
        result.push([i, this.calculateVariant(4800000, 10, i)]);
      }
      return result;
    }
  },
}
</script>

<style>

</style>
