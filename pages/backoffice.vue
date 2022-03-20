<template>
  <div>
    <h1>Gestione Eventi 🎉</h1>
    <div>
        <div class="div-table">
            <b-table hover :items="events" :fields="fields">
                <template #cell(show_details)="row">
                    <b-button size="sm" @click="row.toggleDetails" class="mr-2">
                        Modifica
                    </b-button>
                    <b-button size="sm" @click="row.toggleDetails" class="mr-2" style="background-color: red;">
                        Elimina
                    </b-button>
                </template>
            </b-table>
        </div>
        <b-button size="sm" @click="click()" class="mr-2" style="background-color: green;">Aggiungi Evento</b-button>

        <!-- use the modal component, pass in the prop -->
        <modal :show="showModal" @close="showModal = false" @confirm="postEvent" class="modal">
            <template #header>
                <h3>Inserisci Evento 🌠</h3>
            </template>
            <template #body>
                  <b-row class="my-1" style="text-align: left;">
                    <b-col>
                        <label class="input-desc mb-2">Tipo:</label>
                        <b-form-input id="input-valid" :state="true" placeholder="Inserisci"></b-form-input>
                    </b-col>
                    <b-col>
                        <label class="input-desc mb-2">Data:</label>
                        <b-form-input id="input-valid" :state="true" placeholder="Inserisci"></b-form-input>
                    </b-col>
                    <b-col>
                        <label class="input-desc mb-2">Descrizione:</label>
                        <b-form-input id="input-valid" :state="true" placeholder="Inserisci"></b-form-input>
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
        model: {type: ""}
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
                console.log(events);
            })
            .catch(e => {
                console.log(e);
            })
        },
        click() {
            this.showModal = true;
        },
        postEvent() {
            console.log("Bella pette");
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