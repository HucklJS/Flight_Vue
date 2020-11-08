<template>
  <div id="app">
<!--    <img alt="Vue logo" src="./assets/logo.png">-->
<!--    <HelloWorld msg="Welcome to Your Vue.js App"/>-->
    <FiltersBar
      @change-sort-order="changeSortOrder"
      :sorting-order="sortingOrder"
    />
    <Flights
      :flights-on-page="flightsOnPage"
    />
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import FiltersBar from "./components/FiltersBar"
import Flights from "./components/Flights"
import {result} from "./assets/flights.json"

export default {
  name: 'App',
  components: {
    // HelloWorld,
    FiltersBar,
    Flights
  },
  data() {
    return {
      sortingOrder: 'inc',
      numberOfFlightsPerPage: 2,
      flights: result.flights
    }
  },
  computed: {
    flightsOnPage() {
      return [...this.flights]
        .sort(this._getSortFunction(this.sortingOrder))
        .slice(0, this.numberOfFlightsPerPage)
    }
  },
  methods: {
    changeSortOrder($event) {
      this.sortingOrder = $event.target.value
    },
    _getSortFunction(sortingOrder) {
      switch (sortingOrder) {
        case 'inc':
          return (a, b) => a.flight.price.total.amount - b.flight.price.total.amount
        case 'dec':
          return (a, b) => b.flight.price.total.amount - a.flight.price.total.amount
        case 'time':
          return (a, b) => a.flight.legs.reduce((totalTime, leg) => totalTime + leg.duration, 0)
            - b.flight.legs.reduce((totalTime, leg) => totalTime + leg.duration, 0)
      }
    }
  },
  created() {
    const item = result.flights.find(item => item.flight.price.total.amount === '21049')
    console.log(item)
    console.log(item.flight.legs.reduce((prev, leg) => prev + leg.duration, 0))
    console.log(this.flightsOnPage)
  }
}
</script>

<style>
* {
  box-sizing: border-box;
}
body {
  margin: 0;
}
#app {
  /*font-family: Avenir, Helvetica, Arial, sans-serif;*/
  /*-webkit-font-smoothing: antialiased;*/
  /*-moz-osx-font-smoothing: grayscale;*/
  /*text-align: center;*/
  /*color: #2c3e50;*/
  /*margin-top: 60px;*/
  display: flex;
  font-size: 14px;
  min-height: 100vh;
}
</style>
