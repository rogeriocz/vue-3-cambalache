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
                <input id="title" type="text" class="form-control">
              </div>

              <div class="form-group">
                <label for="type">Tipo</label> 
                <select id="type" class="form-control">
                  <option value="">Seleccione tipo</option>
                </select>
              </div>

              <div class="form-group">
                <label for="price_min">Precio</label>
                <div class="input-group">
                  <input type="text" id="price_min" placeholder="Mínimo" class="form-control">
                  <input type="text" id="price_max" placeholder="Máx" class="form-control">
                </div>            
              </div>
            </form>
          </div>
        </div>
        
      </div>

      <div class="col-md-9">
          <div class="row">
            <div class="col-md-3" v-for="post in posts" :key="post.id">
              <Anuncio :title="post.title" :price="223" :imageUrl="post.imageUrl" />
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
      posts: [
        { id: 1, title: 'My journey with Vue', imageUrl: 'https://via.placeholder.com/600x600.png/006600?text=technics+numquam' },
        { id: 2, title: 'Blogging with Vue', imageUrl: 'https://via.placeholder.com/600x600.png/006600?text=technics+ABC' },
        { id: 3, title: 'Why Vue is so fun', imageUrl: 'https://via.placeholder.com/600x600.png/006600?text=technics+DEF' }
      ],
      showModal: false
    }
  }
}
</script>


