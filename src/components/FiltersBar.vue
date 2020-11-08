<template>
  <aside>
    <div class="aside-content">
      <div class="sorting-block block" @change="$emit('change-sort-order', $event)">
        <span class="block-title">Сортировка</span>
        <label><input
          type="radio" value="inc" class="sorting-radio" name="sort" :checked="sortingOrder==='inc'"
        ><span> - по возрастанию цены</span></label>
        <label><input
          type="radio" value="dec" class="sorting-radio" name="sort" :checked="sortingOrder==='dec'"
        ><span> - по убыванию цены</span></label>
        <label><input
          type="radio" value="time" class="sorting-radio" name="sort" :checked="sortingOrder==='time'"
        ><span> - по времени в пути</span></label>
      </div>

      <div class="filtering-block block">
        <span class="block-title">Фильтровать</span>
        <label><input type="checkbox" class="sorting-checkbox" name="with"><span> - 1 пересадка</span></label>
        <label><input type="checkbox" class="sorting-checkbox" name="without"><span> - без пересадок</span></label>
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
    props: {
      sortingOrder: String
    }
  }
</script>

<style scoped>
aside {
  min-width: 250px;
  padding: 30px 0 70px;
  background-color: lightgrey;
}

.aside-content {
  position: fixed;
  min-width: 250px;
  background-color: white;
  padding: 0.5rem;
}

.block {
  margin-bottom: 1rem;
}

.block-title {
  display: block;
  margin-bottom: 15px;
}

.sorting-block {
  display: block;
}

label {
  display: block;
}

.sorting-input {
  margin-left: 20px;
  margin-bottom: 5px;
}
</style>