<template>
  <div class="container">
    <h1 style="margin-bottom: 10px">Giovani del nuovo mondo 👋</h1>
    <h4 style="margin-bottom: 60px; font-weight: lighter;">Eventi di {{mese}}</h4>
    
    <div class="div-card" v-for="event in events" >
            <b-card 
              class="card-plus" 
              border-variant="" 
              :header="event.type"
              align="center"
              >
              <b-card-text class="card-date">{{event.date}}</b-card-text>
              <b-card-text class="card-body">{{event.description}}</b-card-text>
            </b-card>       
    </div>
</div>
  </div>
</template>

<script>

let jsonEvents = [
   {
      "_id":"62379a91ecefe08f59ceb2a8",
      "type":"dxczv",
      "date":"xczvxc",
      "description":"zxcvxc"
   },
   {
      "_id":"62379bae4b6fb88ea3d907cb",
      "type":"Cena",
      "date":"23-03-2022",
      "description":"CEna a base di pizza ore 21.00"
   },
   {
      "_id":"62379c0c4b6fb88ea3d907cc",
      "type":"Festa",
      "date":"29-03-2022",
      "description":"DJ set e karaoke"
   },
   {
      "_id":"623b7ca63503b28e8b6c7590",
      "type":"Cena",
      "date":"31-03-2022",
      "description":"Cena presso ristorante Vegano Raw Vegan - Firenze ore 21.30"
   },
   {
      "_id":"623c4764d6b03815673dbebc",
      "type":"Riunione",
      "date":"03/04/2022",
      "description":"Riunione organizzativa ore 21.30"
   }
]

import axios from 'axios'
export default {
    data() {
      return {
        events: [],
        mese: ""
      }
    },

    methods:{
      getUnits: function() {
        /*axios.get(`http://localhost:8080/events`)
          .then(response => {
            // JSON responses are automatically parsed.
            //this.events = response.data
            this.events = response.data;
            console.log(events);
          })
          .catch(e => {
            console.log(e);
          })*/
          this.events = jsonEvents;
      }
    },
    beforeMount(){
        this.getUnits()
    },
    
    // on page change 
    async fetch() {
      /*axios.get(`http://localhost:8080/month`)
          .then(response => {
            this.mese = response.data.month;
            console.log(mese);
          })
          .catch(e => {
            console.log(e);
          })*/
          this.mese = 'Aprile';
      /*axios.get(`http://localhost:8080/events`)
          .then(response => {
            // JSON responses are automatically parsed.
            //this.events = response.data
            this.events = response.data;
            console.log(events);
          })
          .catch(e => {
            console.log(e);
          })*/
          this.events = jsonEvents;
    }
}
</script>
<style>
.div-card {
  display: flex; 
  justify-content: center; 
  flex-flow: wrap;
  margin-bottom: 60px;
}
.card-plus {
  width: 800px;
  height: 300px;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
  border-color: #1C658C !important;
  font-size: x-large;
}
.card-body{
  justify-content: center;
  display: flex;
  flex-flow: column;
  background-color: #EEEEEE !important;
}


.card-header {
  background-color: #398AB9 !important;
  color: white
}

</style>
