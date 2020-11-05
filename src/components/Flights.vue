<template>
  <main>
    <div class="flight-card">
      <div class="flight-header">
        <div class="logo">logo</div>
        <div class="price"><strong class="price-value">48544р </strong> стоимость для одного взрослого пассажира </div>
      </div>
      <div class="ticket">
        <div class="flight-route">Москва Шереметьево (SVO) - Лондон Хитроу (LHR)</div>
        <div class="flight-time">
          <div class="date">
            <span class="time">20:40</span>
            <span class="day">18 авг. вт</span>
          </div>
          <span class="in-road-time">14ч. 45 мин.</span>
          <div class="date">
            <span class="day">19 авг. ср.</span>
            <span class="time">09:25</span>
          </div>
        </div>
        <div class="transfer">1 пересадка</div>
<!--        <hr class="transfer-line" v-else>-->
        <div class="flight-company">Рейс выполняет Аэрофлот</div>
      </div>
      <hr class="between-tickets">
      <div class="ticket">
        <div class="flight-route">Лондон Хитроу (LHR) - Москва Шереметьево (SVO)</div>
        <div class="flight-time">
          <div class="date">
            <span class="time">20:40</span>
            <span class="day">18 авг. вт</span>
          </div>
          <span class="in-road-time">14ч. 45 мин.</span>
          <div class="date">
            <span class="day">19 авг. ср.</span>
            <span class="time">09:25</span>
          </div>
        </div>
        <div class="transfer">1 пересадка</div>
        <div class="flight-company">Рейс выполняет Аэрофлот</div>
      </div>
      <a href="https://www.google.com/" class="order-page">Заказать</a>
    </div>
  </main>
</template>

<script>
  export default {}
</script>

<style scoped>
  main {
    padding-left: 20px;
  }

  .flight-card {
    margin-top: 20px;
    min-width: 600px;
  }

  .flight-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: dodgerblue;
    color: white;
  }
  
  .price {
    padding: 5px 10px;
    text-align: right;
  }
  .price-value {
    display: block;
    font-size: 1.2rem;
  }

  .ticket {
    margin: 12px 8px 0;
    padding: 6px 0;
  }
  .flight-route {
    padding: 5px 0;
    margin-bottom: 10px;
    border-bottom: 1px solid rgba(0, 0, 0, 0.2);
  }
  .flight-time {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 10px;
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
    margin-bottom: 10px;
    font-size: 0.9em;
  }

  .between-tickets {
    height: 2px;
    background-color: dodgerblue;
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
</style>