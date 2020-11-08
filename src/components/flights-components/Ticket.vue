<template>
  <div class="ticket">
    <div class="flight-route">
      {{departureCity}}, {{departureAirport}} (SVO) - {{arrivalCity}}, {{arrivalAirport}} (LHR)
    </div>
    <div class="flight-time">
      <div class="date">
        <span class="time">{{getTime(departureDate)}}</span>
        <span class="day">{{getDay(departureDate)}}</span>
      </div>
      <span class="in-road-time">{{getDuration(duration)}}</span>
      <div class="date">
        <span class="day">{{getDay(arrivalDate)}}</span>
        <span class="time">{{getTime(arrivalDate)}}</span>
      </div>
    </div>
    <div class="transfer" v-if="transfers">1 пересадка</div>
    <hr class="transfer-line" v-else>
    <div class="flight-company">Рейс выполняет {{carrier}}</div>
  </div>

<!--  <div class="ticket">-->
<!--    <div class="flight-route">Лондон Хитроу (LHR) - Москва Шереметьево (SVO)</div>-->
<!--    <div class="flight-time">-->
<!--      <div class="date">-->
<!--        <span class="time">20:40</span>-->
<!--        <span class="day">18 авг. вт</span>-->
<!--      </div>-->
<!--      <span class="in-road-time">14ч. 45 мин.</span>-->
<!--      <div class="date">-->
<!--        <span class="day">19 авг. ср.</span>-->
<!--        <span class="time">09:25</span>-->
<!--      </div>-->
<!--    </div>-->
<!--    <div class="transfer">1 пересадка</div>-->
<!--    <div class="flight-company">Рейс выполняет Аэрофлот</div>-->
<!--  </div>-->

</template>

<script>
  export default {
    props: [
      'departureCity',
      'departureAirport',
      'arrivalCity',
      'arrivalAirport',
      'departureDate',
      'arrivalDate',
      'duration',
      'transfers',
      'carrier'
    ],

    methods: {
      getTime(strDate) {
        console.log(strDate)
        console.log('Date.parse(strDate): '+Date.parse(strDate))
        console.log(new Date(Date.parse(strDate)))
        const date = new Date(Date.parse(strDate))

        return `${date.getHours()}:${date.getMinutes()}`
      },
      getDay(strDate) {
        const months = ['янв', 'фев', 'мар', 'апр', 'мая', 'июн', 'июл', 'авг', 'сен', 'окт', 'ноя', 'дек']
        const days = ['вс', 'пн', 'вт', 'чт', 'пт', 'сб']
        const date = new Date(Date.parse(strDate))

        return `${date.getDate()} ${months[date.getMonth()]}. ${days[date.getDay()]}`
      },
      getDuration(minutes) {
        const hours = Math.floor(minutes / 60)
        const mins = minutes % 60

        return `${hours} ч ${mins} мин`
      },
    }
  }
</script>

<style>
  .ticket {
    margin: 12px 0 0;
    padding: 6px 8px;
  }
  .ticket:nth-child(2) {
    border-bottom: 2px solid dodgerblue;
  }
  .flight-route {
    padding: 10px 0;
    margin-bottom: 15px;
    border-bottom: 1px solid rgba(0, 0, 0, 0.2);
  }
  .flight-time {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 15px;
  }

  .date{
    display: flex;
    align-items: flex-end;
  }
  .date :first-child {
    margin-right: 8px;
  }
  .day {
    font-size: 0.6rem;
    color: dodgerblue;
  }

  .transfer {
    width: 90%;
    margin: 10px auto;
    text-align: center;
    font-size: .5rem;
    color: orange;
    overflow: hidden;
  }
  .transfer:before,
  .transfer:after,
  hr.transfer-line {
    content: "";
    position: relative;
    display: inline-block;
    height: 1px;
    width: 100%;
    vertical-align: middle;
    background-color: black;
  }
  hr.transfer-line {
    width: 90%;
    margin: 0 5% 0 5%;
  }
  .transfer:before {
    left: -14px;
    margin-left: -100%;
  }
  .transfer:after {
    right: -14px;
    margin-right: -100%;
  }

  .flight-company {
    margin-bottom: 5px;
    font-size: 0.9em;
  }
</style>