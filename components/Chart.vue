<template>
  <section class="chart">
      <div class="container">
          <div class="row">
            <h4>Cases per day (last 7 days)</h4>
              <div class="chart-conatiner" style="width: 100%">
                <chart-line v-if="data" :data="data" :options="options"/>
              </div>
          </div>
          <div class="row">
            <a href="https://www.gov.uk/coronavirus" target="_blank">VIEW IN DETAILS</a>
          </div>
      </div>
  </section>
</template>
<script>
export default {
  props: ["covidWeeklyCases"],
  data() {
    return {
      options: {
        responsive: true,
        bezierCurve: false,
        legend: {
          display: false
        },
        maintainAspectRatio: false,
        elements: {
          line: {
            tension: 0
          }
        },
        scales: {
          xAxes: [{
            gridLines: {
              color: "rgba(0, 0, 0, 0)",
            },
            ticks: {
              maxRotation: 0,
              minRotation: 0
            }        
          }],
          yAxes: [{
            gridLines: {
              color: "rgba(0, 0, 0, 0)",
            },
            ticks: {
              min: 0,
              max: 40000,
              stepSize: 10000
            }
          }]
        }
      }
    }
  },
  computed: {
    data() {
      let newCases = [];
      let labels = []
      this.covidWeeklyCases.reverse();
      this.covidWeeklyCases.map(el => {
        const date = this.$moment(el.date).format("D/M");
        labels.push(date);
        newCases.push(el.newCases);
      });
      let data = {
        labels: labels,
        datasets: [{
          data: newCases,
          backgroundColor: ["#FFEFEF"],
          borderColor: ["#EB5757"],
          borderWidth: 2,
          pointBorderWith: 4,
          pointBorderColor: "#EB5757",
          pointBackgroundColor: "#EB5757"
        }],
      };
      return data;
    }
  },
};
</script>
<style lang="scss" scoped>
  h4 {
    margin-bottom: 30px;
  }
  .row:last-of-type {
    margin-top: 100px;
    justify-content: center;
    a {
      text-decoration: none;
      padding: 10px 20px;
      border-radius: 5px;
      font-size: 1.4rem;
      border: 2px solid #333333;
      color: #333333;
      text-transform: uppercase;
      transition: all .2s ease-in-out;

      &:hover {
        transition: all .2s ease-in-out;
        background: #333333;
        color: white;
      }
    }
  }
</style>
