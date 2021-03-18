<template>
  <div class="main">
    <template v-if="flightsOnPage.length">
      <div
        class="flight-card"
        v-for="f in flightsOnPage"
        :key="f.flightToken"
      >
        <div class="flight-header">
          <div class="logo">{{f.flight.carrier.airlineCode}} logo</div>
          <div class="price">
            <strong class="price-value">{{f.flight.price.total.amount}}</strong> стоимость для одного взрослого пассажира
          </div>
        </div>
        <Ticket
          v-for="leg in f.flight.legs"
          :key="leg.duration"

          :departure-city="leg.segments[0].departureCity.caption"
          :departure-airport="leg.segments[0].departureAirport.caption"
          :arrival-city="leg.segments[leg.segments.length - 1].arrivalCity.caption"
          :arrival-airport="leg.segments[leg.segments.length - 1].arrivalAirport.caption"

          :departure-date="leg.segments[0].departureDate"
          :arrival-date="leg.segments[leg.segments.length - 1].arrivalDate"
          :duration="leg.duration"

          :transfers="leg.segments.length - 1"

          :carrier="f.flight.carrier.caption"
        />
        <a href="https://www.google.com/" class="order-page">Заказать</a>
      </div>

      <button
        class="show-more-flights"
        @click="$emit('increase-number-of-flights-per-page')"
      >Показать еще</button>
    </template>
    <div v-else class="no-flights">По этим фильтрам отображать нечего:(</div>
  </div>
</template>

<script>
  import Ticket from "./flights-components/Ticket"
  export default {
    components: {
      Ticket
    },
    props: {
      flightsOnPage: Array
    }
  }
</script>

<style scoped>
  .main {
    padding-left: 20px;
  }

  .flight-card {
    margin: 20px 0;
    min-width: 600px;
  }

  .flight-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 5px 10px;
    background-color: dodgerblue;
    color: white;
  }
  
  .price {
    text-align: right;
  }
  .price-value {
    display: block;
    font-size: 1.2rem;
  }

  .order-page {
    display: block;
    width: 100%;
    padding: .75em;
    background-color: orange;
    color: white;
    text-align: center;
    text-decoration: none;
  }

  .show-more-flights {
    display: block;
    margin: 30px auto;
  }
</style>