<template>
  <div class="d-flex flex-column flex-md-row align-items-center p-3 px-md-4 mb-0 bg-white border-bottom box-shadow">
      <h5 class="my-0 mr-md-auto text-center font-weight-normal">Cambalache</h5>
      
      <button class="btn btn-primary" @click="showModal = true">
        Contáctanos
      </button>
  </div>

  <section class="container-fluid mt-4">
    <div class="row">
      <div class="col-md-2">
        <div class="card">
          <div class="card-body">
            <p>Buscador de anuncios empresarial entre trabajadores</p>
                
            <form>
              <div class="form-group">
                <label for="title">Anuncio</label>
                <input id="title" type="text" class="form-control" v-model="query.title" @keyup="onTitleKeyUp">
              </div>

              <div class="form-group">
                <label for="type">Tipo</label> 
                <select id="type" class="form-control" @change="onTypeChanged" v-model="query.type_id">
                  <option value="">Seleccione tipo</option>
                  <option v-for="type in types" :value="type.id" :key="type.id">{{ type.name }}</option>
                </select>
              </div>

              <div class="form-group">
                <label for="price_min">Precio</label>
                <div class="input-group">
                  <input type="number" id="price_min" placeholder="Mínimo" class="form-control" v-model="query.price_min" @keyup="onPriceMinKeyUp">
                  <input type="number" id="price_max" placeholder="Máx" class="form-control" v-model="query.price_max" @keyup="onPriceMaxKeyUp">
                </div>
              </div>
            </form>
          </div>
        </div>
        
      </div>

      <div class="col-md-9">
          <div class="row">
            <div class="col-md-3" v-for="anuncio in anuncios" :key="anuncio.id">
              <Anuncio 
                :title="anuncio.title" 
                :price="anuncio.price" 
                :typeName="anuncio.type_name"
                :imageUrl="anuncio.image" />
            </div>
          </div>
      </div>
    </div>
  </section>

  <Modal v-if="showModal" @close="showModal = false" />
</template>

<script>
import Anuncio from './components/Anuncio.vue'
import Modal from './components/Modal.vue'

export default {
  name: 'App',

  components: {
    Anuncio, Modal
  },

  data() {
    return {
      anuncios: [
        { id: 1, title: 'Por favor espere', imageUrl: 'https://via.placeholder.com/600x600.png/006600?text=Cargando ...' }
      ],
      showModal: false,
      types: [],
      query: {
        title: '',
        type_id: '',
        price_min: '',
        price_max: ''
      }
    }
  },

  mounted() {
    this.fetchTypes();
    this.fetchAnuncios();
  },

  methods: {
    onTypeChanged() {
      console.log('onTypeChanged');
      this.fetchAnuncios();
    },
    onTitleKeyUp() {
      console.log('onTitleChanged');
      this.fetchAnuncios();
    },
    onPriceMinKeyUp() {
      console.log('onPriceMinKeyUp');
      this.fetchAnuncios();
    },
    onPriceMaxKeyUp() {
      console.log('onPriceMaxKeyUp');
      this.fetchAnuncios();
    },

    fetchTypes() {
      fetch('http://apicambalache.test/api/types')
      .then(response => response.json())
      .then(data => {
        this.types = data;
      });
    },

    fetchAnuncios() {
      const queryParams = new URLSearchParams(this.query);
      const urlAnuncios = 'http://apicambalache.test/api/anuncios?' + queryParams;

      fetch(urlAnuncios)
      .then(response => response.json())
      .then(data => {
        this.anuncios = data;
      });
    }
  }
}
</script>
