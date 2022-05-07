<template>
  <div class="container">
    <h1 style="margin-bottom: 10px">Giovani del Nuovo Mondo</h1>
    <h3 style="margin-bottom: 10px"></h3>
    <h4 style="margin-bottom: 60px; font-weight: lighter; font-size: 26px;">Eventi di <span style="font-weight:bolder">{{mese}}</span></h4>
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
      "type":"Serata",
      "date":"6 Maggio 2022",
      "description":"Sera: Street Food Montecatini + bevuta a giro dopo cena."
   },
   {
      "_id":"62379bae4b6fb88ea3d907cb",
      "type":"Svago",
      "date":"7 Maggio 2022",
      "description":"Pomeriggio: Villone svago"
   },
   {
      "_id":"62379c0c4b6fb88ea3d907cc",
      "type":"Gita",
      "date":"8 Maggio 2022",
      "description":"Mattina - pomeriggio: girata fuori porta con pranzo, se disponibile San Quirico più camminata al Borgo."
   },
   {
      "_id":"62379c0c4b6fb88ea3d907cc",
      "type":"Serata",
      "date":"11 Maggio 2022",
      "description":"Pomeriggio tardo: aperitivo bar Tris/centro Pt + ritrovo casa Giovanni a Pt."
   },
   {
      "_id":"62379c0c4b6fb88ea3d907cc",
      "type":"Serata",
      "date":"13 Maggio 2022",
      "description":"Sera: Aperitivo Montemurlo + giro in centro a Prato dopo cena."
   },
    {
      "_id":"62379c0c4b6fb88ea3d907cc",
      "type":"Serata",
      "date":"14 Maggio 2022",
      "description":"Sera: riunione+ successivament e festa alla stalla."
   },
    {
      "_id":"62379c0c4b6fb88ea3d907cc",
      "type":"Serata",
      "date":"20 Maggio 2022",
      "description":"Sera: cena Festa cinghiale a Vicchio di Mugello."
   },
   {
      "_id":"62379c0c4b6fb88ea3d907cc",
      "type":"Svago",
      "date":"21 Maggio 2022",
      "description":"Pomeriggio: partita di pallone ( dare disponibilità entro mercoledì 11 per prenotare un campo ufficiale )."
   },
   {
      "_id":"62379c0c4b6fb88ea3d907cc",
      "type":"Gita",
      "date":"22 Maggio 2022",
      "description":"Mattina-sera: giornata al mare, location da decidere."
   },
   {
      "_id":"62379c0c4b6fb88ea3d907cc",
      "type":"Serata",
      "date":"27 Maggio 2022",
      "description":"Sera: cena Lucca street food/ristorante + giro dopo cena in centro"
   },
   {
      "_id":"62379c0c4b6fb88ea3d907cc",
      "type":"Svago & Serata",
      "date":"28 Maggio 2022",
      "description":"Pomeriggio: Villone svago. Sera: festa alla stalla."
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
          this.mese = 'Maggio';
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
  text-shadow: -1px 0 black, 0 2px black, 0px 0 black, 0 0px black;

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
