<template>
  <li>
    
    <p>Дата: {{ gasStation.datastart }}</p>

    <p>Лот: <input type="value" v-model.value="nnewAuction.rest_name" /></p>
    <p>Початок торгів: <input type="data" v-model.data="newAuction.rest_start_auction" /></p>
    <p>Кінець торгів: <input type="number" v-model.number="newAuction.rest_end_auction" /></p>

    <p> Ціна на початку торгів: <input type="number" v-model.number="newAuction.price_start" />грн.</p>
    <p>Ціна після закінчення торгів: <input type="number" v-model.number="newAuction.price_end" /> грн.</p>

  </li>
</template>

<script>
export default {
  name: "auction",
  props: {
    auction: Object,
  },
  data() {
    return {};
  },
};
</script>

<style scoped>
</style>>

