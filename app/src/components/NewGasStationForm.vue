<template>
 <form
        v-on:submit.prevent="addNewAuction"
        class="newForm"
        v-if="showNewAuctionForm"
      >
        
      Дата: <input v-model="newAuction.datastart" /> <br />

      Лот: <input type="value" v-model.value="nnewAuction.rest_name" /> <br />
        Початок торгів: <input type="data" v-model.data="newAuction.rest_start_auction" /> <br />
        Кінець торгів: <input type="number" v-model.number="newAuction.rest_end_auction" /> <br />

        Ціна на початку торгів: <input type="number" v-model.number="newAuction.price_start" /> <br />
        Ціна після закінчення торгів: <input type="number" v-model.number="newAuction.price_end" /> <br />

        <button type="submit">Додати</button>
        <button type="reset">Очистити</button>
      </form>
</template>

<script>
export default {
  name: "NewAuction",
  props: {
    modelValue: Object,
  },
  data() {
    return {
        showNewAuctionForm:false,
        newAuction : this.modelValue,
    };
  },
   methods:{
        
        addNewAuction(){
            this.$emit("update:modelValue", this.newAuction); 
            this.hide();
        }, 
        show(){
            this.showNewAuctionForm = true;
        },
        hide(){
            this.showNewAuctionForm = false;
        }
    }, 
};
</script>

<style scoped>
</style>>
