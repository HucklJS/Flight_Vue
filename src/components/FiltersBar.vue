<template>
  <aside>
    <div class="aside-content">
      <div class="sorting-block block">
        <span class="block-title">Сортировка</span>
        <label><input type="radio" class="sorting-radio" name="sort"><span> - по возрастанию цены</span></label>
        <label><input type="radio" class="sorting-radio" name="sort"><span> - по убыванию цены</span></label>
        <label><input type="radio" class="sorting-radio" name="sort"><span> - по времени в пути</span></label>
      </div>

      <div class="filtering-block block">
        <span class="block-title">Фильтровать</span>
        <label><input type="checkbox" class="sorting-checkbox" name="inc"><span> - по возрастанию цены</span></label>
        <label><input type="checkbox" class="sorting-checkbox" name="dec"><span> - по убыванию цены</span></label>
        <label><input type="checkbox" class="sorting-checkbox" name="time"><span> - по времени в пути</span></label>
      </div>

      <div class="price-block block">
        <span class="block-title">Цена</span>
        <label><span>От</span><input class="sorting-input" name="from"></label>
        <label><span>До</span><input class="sorting-input" name="to"></label>
      </div>

      <div class="avia-companies-block block">
        <span class="block-title">Авиакомпании</span>
        <label><input type="checkbox" class="sorting-checkbox" name="aeroflot"><span> - Аэрофлот</span></label>
        <label><input type="checkbox" class="sorting-checkbox" name="polish-airlines"><span> - Polish airlines</span></label>
      </div>
    </div>
  </aside>
</template>

<script>
  export default {

  }
</script>

<style scoped>
aside {
  min-width: 250px;
  padding: 30px 0 70px;
  background-color: lightgrey;
}

.aside-content {
  background-color: white;
  padding: 0.5rem;
}

.block {
  margin-bottom: 1rem;
}

.sorting-block {
  display: block;
}

label {
  display: block;
}

.sorting-input {
  margin-left: 20px;
}
</style>