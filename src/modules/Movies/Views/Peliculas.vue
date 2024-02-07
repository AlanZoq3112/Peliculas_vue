<template>
  <div class="body">
    <div>
      <b><h3>Peliculas</h3></b>
    </div>

    <div>
      <b-modal hide-footer hide-header centered id="modal-save-movie">
        <header class="text-center border-bottom">
          <p style="font-family: cabin">Registrar pelicula</p>
        </header>

        <main>
          <form id="registrarPelicula">
            <b-row>
              <b-col>
                <label for="pelicula">Nombre de la pelicula: *</label>
                <b-form-input
                  v-model="pelicula.name"
                  type="text"
                  class="form-control"
                  placeholder="Pelicula..."
                  required
                  aria-describedby="input-live-help input-live-feedback"
                />
                <b-form-invalid-feedback>
                  ingresa un nombre de usuario válido
                </b-form-invalid-feedback>
              </b-col>
              <b-col>
                <label for="pelicula">Genero de la pelicula: *</label>
                <b-form-select
                  v-model="pelicula.genero"
                  :options="options"
                ></b-form-select>
              </b-col>
            </b-row>
            <b-row>
              <b-col>
                <label for="pelicula">Descripción de la pelicula: *</label>
                <b-form-textarea
                  id="textarea"
                  v-model="pelicula.description"
                  placeholder="Describe la pelicula..."
                  rows="3"
                  max-rows="6"
                ></b-form-textarea>
              </b-col>
            </b-row>
          </form>
        </main>

        <footer class="text-center mt-5">
          <button class="btn m-1 cancel" @click="onClose" id="savemovie">
            Cancelar
          </button>
          <button
            class="btn m-1 success"
            @click="save"
            id="saveteam"
            type="submit"
          >
            Registrar
          </button>
        </footer>
      </b-modal>
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
            <b-card
              title="Card Title"
              img-src="https://picsum.photos/600/300/?image=25"
              img-alt="Image"
              img-top
              tag="article"
              style="max-width: 20rem"
              class="mb-2"
            >
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
    </div>
  </div>
</template>
  
  <script>
export default {
  name: "pelis",

  data() {
    return {
      pelicula: {
        name: "",
        description: "",
        genero: null,
      },
      selected: null,
      options: [
        { value: null, text: "Selecciona una opción" },
        { value: "Terror", text: "Terror" },
        { value: "Aventura", text: "Aventura" },
        { value: "Acción", text: "Acción" },
        { value: "Catástrofe", text: "Catástrofe" },
        { value: "Ciencia Ficción.", text: "Ciencia Ficción." },
        { value: "Comedia", text: "Comedia" },
        { value: "Documentales", text: "Documentales" },
        { value: "Drama", text: "Drama" },
      ],
    };
  },

  methods: {
    onClose() {
      this.$bvModal.hide("modal-save-movie");
      this.pelicula.name=""
      this.pelicula.description=""
      this.pelicula.genero=null

    },
    async save() {
      console.log(this.pelicula);
    },
  },
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
.success {
  font-family: Cabin;
  background-color: #009475;
  color: white;
}
.cancel {
  font-family: Cabin;
  background-color: #ffce50;
  color: black;
}
</style>