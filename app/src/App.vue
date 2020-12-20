
<template>
  <div>
    Вибрано аукціон {{ selected }}
    <input type="button" value="Додати" v-on:click="showForm" />
    <input type="button" value="Редагувати" v-on:click="showEditForm" />
    <input type="button" value="Вилучити" v-on:click="deleteGasStation" />
    <input type="button" value="Знайти" v-on:click="showFindGasStationOwner" />
    <div class="wrap">
      <form
        v-on:submit.prevent="addnewAuction"
        class="newForm"
        v-if="showNewAuctionForm"
      >
         
        Дата: <input v-model="newAuction.datastart" /> <br />

        Лот:
        <input type="value" v-model.value="nnewAuction.rest_name" /> <br />
        Початок торгів:
        <input type="data" v-model.data="newAuction.rest_start_auction" /> <br />
        Кінець торгів:
        <input type="number" v-model.number="newAuction.rest_end_auction" /> <br />

        Ціна на початку торгів:
        <input type="number" v-model.number="newAuction.price_start" /> <br />
        Ціна після закінчення торгів:
        <input type="number" v-model.number="newAuction.price_end" /> <br />
        

        <button type="submit">Додати</button>
        <button type="reset">Очистити</button>
      </form>
      <form
        v-on:submit.prevent="editSelectedAuction"
        class="newForm"
        v-if="showEditAuctionForm"
      >
        
      Лот:
        <input type="value" v-model.value="nnewAuction.rest_name" /> <br />
        Початок торгів:
        <input type="data" v-model.data="newAuction.rest_start_auction" /> <br />
        Кінець торгів:
        <input type="number" v-model.number="newAuction.rest_end_auction" /> <br />

        Ціна на початку торгів:
        <input type="number" v-model.number="newAuction.price_start" /> <br />
        Ціна після закінчення торгів:
        <input type="number" v-model.number="newAuction.price_end" /> <br />

        <button type="submit">Редагувати</button>
        <button type="reset">Очистити</button>
      </form>
      <form
        v-on:submit.prevent="findAuction"
        class="newForm"
        v-if="showFindAuction"
      >
        Дата: <input type="data" v-model="datastart"> <br>

        <button type="submit">Знайти</button>
        <button type="reset">Очистити</button>
      </form>
      <ul>
        <li
          v-for="(g, i) in auction"
          :key="i"
          class="station"
          v-on:click="selectAuction(i)"
          :style="i == selected ? 'border:5px solid black' : ''"
        >
          
          <p>Дата: {{ g.datastart }}</p>

          <p>Лот: {{ g.rest_name.toFixed(2) }} л.</p>
          <p>Ціна початку торгів: {{ g.price_start.toFixed(2) }} л.</p>
          <p>Кінцева ціна: {{ g.price_end.toFixed(2) }} л.</p>

         
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      selected: -1,
      showNewAuctionForm: false,
      showEditAuctionForm: false,
      showFindAuction: false,
      auction: {
      
        
        rest_name: "картина",
        rest_start_auction: 2020,11,12,
        rest_end_auction: 2020,11,14,
        price_start: 150,
        price_end:600,
        
      },
      auction: [
        {
              
        rest_name: "ваза",
        rest_start_auction: 2020,10,12,
        rest_end_auction: 2020,10,14,
        price_start: 1450,
        price_end:6004,

        },
        {
           
        rest_name: "марка",
        rest_start_auction: 2020,11,14,
        rest_end_auction: 2020,11,16,
        price_start: 850,
        price_end:7090,

        {
          
        rest_name: "ніж",
        rest_start_auction: 2020,11,12,
        rest_end_auction: 2020,11,20,
        price_start: 150,
        price_end:5430,

        },
      ],
      newAuction: {
         
        rest_name: "рукопис",
        rest_start_auction: 2020,11,11,
        rest_end_auction: 2020,11,16,
        price_start: 150,
        price_end:6080,

      },
      editAuction: null,
     
    };
  },

  methods: {
    
    addnewAuction() {
      let newGasAuctionCopy = Object.assign({}, this.newAuction);
      this.auction.push(newAuctionCopy);
      this.showNewAuctionForm = false;
    },
    showForm() {
     this.showNewAuctionForm = !this.showNewAuctionForm;
    },
    selectAuction(index) {
      this.selected = index;
    },
    showEditForm() {
      if (this.selected >= 0) {
        this.editAuction = this.auction[this.selected];
        this.showEditAuctionForm = !this.showEditAuctionForm;
      } else alert("Виберіть дату");
    },
    editSelectedAuction() {
      this.showEditAuctionForm = false;
    },
    deleteAuction() {
      if (this.selected >= 0) this.auction.splice(this.selected, 1);
    },
    showFindAuctionOwner(){
      this.showFindAuctionForm = !this.showFindAuctionForm;
    },
    findAuctionOwner(){
      var data = this.data;
      let  name = " ";
      let price_start = 0;
      let price_end = 0;
      var info=this.auction.filter(x=>x.firm_owner===f_o);

      for(var i = 0; i < info.length; i++){
      name+=info[i].rest_name*1;
        price_start+=info[i].price_start*1;
        price_end+=info[i].price_end*1;
        }
        alert("Лот - "+name.toString()+",початкова ціна - "+price_start.toString()+",кінцева ціна - "+price_end.toString()+"  ");
     

      this.showFindWorkerForm=false;
    },
  },
};
</script>



<style scoped>

.station {
  background:goldenrod;
  width: 200px;
  position: relative;
  float: left;
}

</style>