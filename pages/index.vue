<template>
  <main>
   <TopBanner />
   <CasesBanner :covidWeeklyCases="covidWeeklyCases" />
   <Chart :covidWeeklyCases="covidWeeklyCases" />
   <BottomBanner />
   <TheFooter />
  </main>
</template>

<script>
import TopBanner from '../components/TopBanner';
import CasesBanner from '../components/CasesBanner';
import Chart from '../components/Chart';
import BottomBanner from '../components/BottomBanner';
import TheFooter from '../components/TheFooter';
import axios from 'axios';
export default {
  components: {TopBanner, CasesBanner, Chart, BottomBanner, TheFooter},
  data() {
    return {

    }
  },
  asyncData() {
    const mainApiPoint='https://api.coronavirus.data.gov.uk/v1/data';
    const filters = '?filters=areaType=nation;areaName=england';
    const structure = '&structure={%22date%22:%22date%22,%22newCases%22:%22newCasesByPublishDate%22}';
    return axios.get(`${mainApiPoint}${filters}${structure}`)
    .then(response => {
      const weekDay = 7;
      const covidWeeklyCases = response.data.data.slice(0, weekDay)
      return {
        covidWeeklyCases
      }
    })
  },
  
}
</script>

<style>



</style>
