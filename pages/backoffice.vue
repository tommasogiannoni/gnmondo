<template>
  <div>
    <h1>Gestione Eventi 🎉</h1>
    <div>
        <div class="div-table">
            <b-table hover :items="events" :fields="fields" show-empty>
                <template #cell(show_details)="row">
                    <b-button size="sm" @click="modifica(row)" class="mr-2">
                        Modifica
                    </b-button>
                    <b-button size="sm" @click="elimina(row)" class="mr-2" style="background-color: red;">
                        Elimina
                    </b-button>
                </template>
                <template #empty="scope">
                    <p>Non sono stati trovati eventi</p>
                </template>
            </b-table>
        </div>
        <b-button size="sm" @click="click()" class="mr-2" style="background-color: #398AB9;">Aggiungi Evento</b-button>

        <!-- use the modal component, pass in the prop -->
        <modal :show="showModal" @close="showModal = false" @confirm="postEvent" class="modal">
            <template #header>
                <h3>Inserisci Evento 🌠</h3>
            </template>
            <template #body>
                  <b-row class="my-1" style="text-align: left;">
                    <b-col>
                        <label class="input-desc mb-2">Tipo:</label>
                        <b-form-input v-model="model.type" placeholder="Inserisci"></b-form-input>
                    </b-col>
                    <b-col>
                        <label class="input-desc mb-2">Data:</label>
                        <b-form-input v-model="model.date" placeholder="Inserisci"></b-form-input>
                    </b-col>
                </b-row>
                <b-row style="text-align: left; margin-top: 10px" > 
                    <b-col>
                        <label class="input-desc mb-2">Descrizione:</label>
                        <b-form-textarea v-model="model.description" max-rows="5" placeholder="Inserisci"></b-form-textarea>
                    </b-col>
                </b-row>
            </template>
            <template #footer>
            </template>
        </modal>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import Modal from './events-modal.vue'


export default {
    data() {
      return {
        fields: ['type', 'date', 'description', 'show_details'],
        events: [],
        showModal: false,
        model: {type: "", date: "", description: ""},
        scope: true
      }
    },

    components: {
        Modal
    },
    methods:{
         getUnits: function() {
            axios.get(`http://localhost:8080/events`)
                .then(response => {
                    // JSON responses are automatically parsed.
                    //this.events = response.data
                    this.events = response.data;
                    console.log(this.events);
                })
                .catch(e => {
                    this.scope = true;
                    console.log(e);
                })
        },
        click() {
            this.showModal = true;
        },
        elimina(rowItem) {
            console.log("Elimina: ", rowItem);
            let req = this.model;
            axios.delete('http://localhost:8080/event/'+rowItem.item._id, req)
                .then( res => {
                    console.log("Res", res);
                })
                .catch(e => {
                    console.log(e);
                })
            
        },
        modifica(rowItem) {
           console.log("Modifica: ", rowItem); 
        },
        postEvent() {
            if( this.model.type != "" && this.model.date && this.model.description ) {

                let req = this.model;
                axios.post(`http://localhost:8080/event`, req)
                    .then(response => {
                        // JSON responses are automatically parsed.
                        //this.events = response.data
                        this.events = response.data;
                        this.getUnits();
                        this.showModal = false;
                    })
                    .catch(e => {
                        console.log(e);
                    })
            }
        }
    },
    beforeMount(){
        this.getUnits()
    },

}

</script>

<style>
.div-table {
  display: flex; 
  justify-content: center; 
  flex-flow: wrap;
  margin-top: 40px;
  margin-bottom: 20px;
}
.input-desc{
    font-weight: bold;
}
</style>