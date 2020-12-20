<template>
     <form
        v-on:submit.prevent="eeditSelectedAuction"
        class="newForm"
        v-if="showEditAuctionForm"
      >
        
        Дата: <input v-model="newAuction.datastart" /> <br />

      Лот: <input type="value" v-model.value="nnewAuction.rest_name" /> <br />
        Початок торгів: <input type="data" v-model.data="newAuction.rest_start_auction" /> <br />
        Кінець торгів: <input type="number" v-model.number="newAuction.rest_end_auction" /> <br />

        Ціна на початку торгів: <input type="number" v-model.number="newAuction.price_start" /> <br />
        Ціна після закінчення торгів: <input type="number" v-model.number="newAuction.price_end" /> <br />

        <button type="submit">Редагувати</button>
        <button type="reset">Очистити</button>
      </form>
</template>

<script>
export default {
    name:"EditAuctionForm", 
    props:{
        modelValue: Object
    },
    data(){
      return {
          showEditAuctionForm: false,
          editAuction: this.modelValue
      } 
    },
    methods:{
        eeditSelectedAuction(){
            this.$emit("update: modelValue", this.editAuction);
            this.hide();
        },
        show(editAuction){
            this.editAuction=editAuction;
            this.showEditAuctionForm=true;
        },
        hide(){
            this.showEditAuctionForm=false;
        }
    }
}
</script>