<template>
  <div id="app">
<!--    <img alt="Vue logo" src="./assets/logo.png">-->
<!--    <HelloWorld msg="Welcome to Your Vue.js App"/>-->
    <FiltersBar
      @change-sort-order="changeSortOrder"
      :sorting-order="sortingOrder"

      @add-to-filters="addToFilters"
      :filters="filters"
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
      filters: [],
      flights: result.flights
    }
  },
  computed: {
    flightsOnPage() {
      return [...this.flights]
        .sort(this._getSortFunction(this.sortingOrder))
        .filter(f => !this.filters.length || this.filters.includes(this._getNumberOfTransfers(f)))
        .slice(0, this.numberOfFlightsPerPage)
    }
  },
  methods: {
    changeSortOrder($event) {
      this.sortingOrder = $event.target.value
    },
    addToFilters($event) {
      const value = $event.target.value
      console.log(value)

      if (this.filters.includes(value)) {
        this.filters = this.filters.filter(filter => filter !== value)
      } else {
        this.filters.push(value)
      }
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
    },
    _getNumberOfTransfers(f) {
      const transfers = f.flight.legs.reduce((transfers, leg) => transfers + leg.segments.length - 1, 0)
      return String(transfers)
    }
  },
  // created() {
  //   const item = result.flights.find(item => item.flight.price.total.amount === '21049')
  //   console.log(item)
  //   console.log(item.flight.legs.reduce((prev, leg) => prev + leg.duration, 0))
  //   console.log(this.flightsOnPage)
  //   console.log(this._getNumberOfTransfers(item))
  // }
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
