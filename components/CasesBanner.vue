<template>
    <section class="casesBanner">
        <div class="container">
            <div class="row">
                <div class="newCases">
                    <div class="average">
                        <img v-if="aboveAverage" :src="require('../assets/images/average.svg')" alt="average" />
                        <p :class="aboveAverage ? null : 'green'">{{aboveAverage ? 'Above average' : 'Below average'}}</p>
                    </div>
                    <div class="newCasesYesterday">
                        <h2 :class="aboveAverage ? null : 'green'">{{newCaseYesterday}}</h2>
                        <p>New Cases Yesterday</p>
                    </div>
                </div>
                <div class="statistics">
                    <div class="outer">
                        <div class="inner-icon">
                            <img :src="require('../assets/images/trending.svg')" alt="trending">
                        </div>
                        <div class="inner-numbers">
                            <h3>{{increase}}%</h3>
                            <p>
                                increase from previews day
                            </p>
                        </div>
                    </div>
                    <div class="outer">
                        <div class="nner-icon">
                            <img :src="require('../assets/images/calendar.svg')" alt="calendar">
                        </div>
                        <div class="inner-numbers">
                            <h3>{{average}}</h3>
                            <p>
                                average of the last 7 days
                            </p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>
<script>
export default {
    props: ['covidWeeklyCases'],
    mounted() {
        if(this.yesterdayNumber > this.averageNumber ) {
            this.aboveAverage = true;
        } else {
            this.aboveAverage = false;
        }
    },
    data() {
        return {
            aboveAverage: false,
            averageNumber: 0,
            yesterdayNumber: this.covidWeeklyCases[0].newCases
        }
    },

    computed: {
        newCaseYesterday() {
            return this.covidWeeklyCases[6].newCases.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
        },
        increase() {
            const firstDay = this.covidWeeklyCases[6].newCases;
            const previousDay = this.covidWeeklyCases[5].newCases;
            const increase = (firstDay - previousDay) / previousDay * 100;
            return increase.toFixed(2)
        },
        average() {
            const arr = [];
            this.covidWeeklyCases.map(el=> {
                arr.push(el.newCases)
            })
            const sum = arr.reduce((p,c)=> p+c, 0)
            const average = sum/arr.length
            this.averageNumber = average
            return average.toFixed(0).toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
        },

    }
}
</script>
<style lang="scss" scoped>
    .newCases {
        padding: 100px 80px;
        display: flex;
        align-items: center;
        justify-content: center;
        background-color: #FFEFEF;
        width: 46%;
        border-radius: 8px;
        box-shadow: 0px 4px 6px -1px rgba(0, 0, 0, 0.1);
        @media only screen and (max-width: 790px) {
            width: 100%;
            margin-bottom: 30px;
        }
        p {
            font-weight: bold;
            color: #5F5F5F;
            font-size: 2.7rem;
        }


        .newCasesYesterday{
            display: flex;
            flex-direction: column;
            align-items: center;
            margin-bottom: 20px;
            h2{
                color: #BB1515;
                font-size: 10rem;
                &.green {
                    color: green;
                }
            }

        }
        .average {
            text-align: center;
            margin-right: 30px;
            p {
                color: #BB1515;

                &.green {
                    color: green;
                }
            }
        }
    }
    .statistics {
        width: 46%;
        @media only screen and (max-width: 790px) {
            width: 100%;
        }

        .outer {
            background: #FAFAFA;
            box-shadow: 0px 3px 10px rgba(0, 0, 0, 0.15);
            padding: 30px 25px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            &:first-of-type {
                margin-bottom: 30px;
            }
            h3 {
                color: black;
            }
            p {
                font-weight: bold;
                color: #5F5F5F;
            }
        }
    }
</style>