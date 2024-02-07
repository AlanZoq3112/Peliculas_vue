<template>
  <div class="body">
    <div>
      <b>
        <h3>Peliculas</h3>
      </b>
    </div>

    <div class="bodybutton">
      <b-button v-b-modal.modal-save-movie class="btnadd">
        <b-icon icon="plus"></b-icon> Agregar pelicula
      </b-button>
    </div>

    <div>
      <b-row>
        <b-col>
          <div>
            <b-card title="Card Title" img-src="https://picsum.photos/600/300/?image=25" img-alt="Image" img-top
              tag="article" style="max-width: 20rem" class="mb-2">
              <b-card-text>
                Some quick example text to build on the card title and make up
                the bulk of the card's content.
              </b-card-text>

              <b-button href="#" variant="primary">Go somewhere</b-button>
            </b-card>
          </div>
        </b-col>
        <b-col>2</b-col>
        <b-col>3</b-col>
        <b-col>4</b-col>
      </b-row>

      <button @click="fetchData">Obtener datos de la API</button>
                    <div v-if="data">
                        <h2>{{ data }}</h2>
                
                    </div>
    </div>

    
    <ModalSaveMovie />
  </div>
</template>
  
<script>
import ModalSaveMovie from '@/modules/Movies/Views/ModalSaveMovie.vue'
import axios from 'axios'
export default {
  components: {ModalSaveMovie},
  name: "pelis",
  data(){
    return{
      data: null
    }
  },
  methods:{
    fetchData() {
        
        axios.get('https://pokeapi.co/api/v2/pokemon/ditto')
            .then(response => {
                this.data = response.data;
            })
            .catch(error => {
                console.error('Error al obtener datos de la API', error);
            });
    }
  }
};
</script>
  
<style scoped>
.body {
  padding-left: 50px;
  padding-right: 50px;
  margin-top: 20px;
}

.bodybutton {
  text-align: end;
}

.btnadd {
  background-color: #089779;
}


</style>