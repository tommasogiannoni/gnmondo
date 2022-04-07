<template>
  <div class="container">
    <h1 style="margin-bottom: 10px">👋 Giovani Nuovo Mondo 👋</h1>
    <h4 style="margin-bottom: 60px; font-weight: lighter;">Eventi di <span style="font-weight:bolder">{{mese}}</span></h4>
    <div class="div-card" v-for="event in events" v-on:click="select($event)">
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
</template>

<script>
let jsonEvents = [
   {
      "_id":"62379a91ecefe08f59ceb2a8",
      "type":"Riunione",
      "date":"8 Aprile 2022",
      "description":"Sera dopo cena: evento Francesco Cappello a Lucca ( sistemi economici alternativi ). Necessità di prenotazione, dare conferma entro 01/04."
   },
   {
      "_id":"62379bae4b6fb88ea3d907cb",
      "type":"Giornata",
      "date":"9 Aprile 2022",
      "description":"Pomeriggio: Villone – incontro sempliceSera: festa di compleanno a casa Maltinti."
   },
   {
      "_id":"62379c0c4b6fb88ea3d907cc",
      "type":"Riunione",
      "date":"15 Aprile 2022",
      "description":"Riunione serale casa Maltinti"
   },
   {
      "_id":"62379c0c4b6fb88ea3d907cc",
      "type":"Giornata",
      "date":"16 Aprile 2022",
      "description":"Gita fuori porta da mattina a sera Firenze, volendo cena presso Raw Vegan"
   },
   {
      "_id":"62379c0c4b6fb88ea3d907cc",
      "type":"Giornata",
      "date":"18 Aprile 2022",
      "description":"Gita fuori porta da mattina a sera al mare, pranzo al sacco"
   },
    {
      "_id":"62379c0c4b6fb88ea3d907cc",
      "type":"Evento",
      "date":"22 Aprile 2022",
      "description":"Aperitivo alle 18 luogo da definire, e-o uscita post cena"
   },
    {
      "_id":"62379c0c4b6fb88ea3d907cc",
      "type":"Giornata",
      "date":"23 Aprile 2022",
      "description":"Girata da mattina a sera: Trekking ed escursione conLeonardo."
   },
   {
      "_id":"62379c0c4b6fb88ea3d907cc",
      "type":"Giornata",
      "date":"25 Aprile 2022",
      "description":"Girata da mattina a sera o solo pomeridiana, luogo da definire ( idea Acquerino, Montagna Pistoiese o Lucca sulle mura)."
   },
   {
      "_id":"62379c0c4b6fb88ea3d907cc",
      "type":"Evento",
      "date":"30 Aprile 2022",
      "description":"Villone nel pomeriggio (o Stalla), Sera: festa di compleanno alla Stalla"
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
      },
      select: function(event) { 
        console.log("Ciaooooo", event); // returns 'foo'
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
  border-radius:30px !important;
  display: flex; 
  justify-content: center; 
  flex-flow: wrap;
  margin-bottom: 60px;
  transition: transform .2s; /* Animation */
}
.div-card:hover {
  transform: scale(1.1); /* (150% zoom - Note: if the zoom is too large, it will go outside of the viewport) */
}

.card-plus {
  border-radius:30px !important;
  width: 800px;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
  border-color: #1C658C !important;
  font-size: x-large;
}
.card-body{
  border-bottom-right-radius:30px !important;
  border-bottom-left-radius:30px !important;
  justify-content: center;
  display: flex;
  flex-flow: column;
  background-color: #EEEEEE !important;
}
.card-header {
  border-top-right-radius:30px !important;
  border-top-left-radius:30px !important;
  height: 80px;  
  display: flex; 
  justify-content: center; 
  align-items: center;
  font-weight: bold;
  font-size: larger;
  text-shadow: -1px 0 black, 0 3px black, 0px 0 black, 0 0px black;

}
.card-date {
  font-weight: lighter;
}
.card-footer {
   border-radius:30px !important;
}
.card-header {
  background-color: #398AB9 !important;
  color: white
}

</style>
