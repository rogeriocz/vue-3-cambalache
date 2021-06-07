<template>
  <transition name="modal">
    <div class="modal-mask">
      <div class="modal-wrapper">
        <div class="modal-container">

          <div class="modal-header">
            Envía un mensaje al administrador
          </div>

          <div class="modal-body">
            <form action="" v-on:submit.prevent="newMessage">
                <div class="form-group">
                    <label for="issuer-name" class="col-form-label">Nombre:</label>
                    <input type="text"  class="form-control" id="issuer-name" v-model="mensaje.name">
                </div>
                <div class="form-group">
                    <label for="message-email" class="col-form-label">Correo:</label>
                    <input type="email"  class="form-control" id="message-email" v-model="mensaje.email">
                </div>
                <div class="form-group">
                    <label for="message-text" class="col-form-label">Mensaje:</label>
                    <textarea  class="form-control" id="message-text" v-model="mensaje.message"></textarea>
                </div>
                <div class="modal-footer">

                  <button type="submit" class="btn btn-primary" >
                    Enviar mensaje
                  </button>  

                  <button class="btn btn-secondary" @click="$emit('close')">
                    Cancelar
                  </button>

              </div>
            </form>
          </div>
            
              

        </div>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  data() {
    return {
      
       mensaje:{}
      
    }
  },

  methods:{
    newMessage() {
      //console.log(this.mensaje);
      var sendData={name:this.mensaje.name, email:this.mensaje.email, message:this.mensaje.message}

      fetch('http://apicambalache.test/api/emails',{
        method:"POST",
        //mode: 'no-cors',
        body:JSON.stringify(sendData),
        headers: {
          "Content-type": "application/json",
        }
      })
      .then(answer => answer.json())
      .then((answerData => {
        console.log(answerData);
      }))
    }
  }
}

</script>

<style scoped>
.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: table;
  transition: opacity 0.3s ease;
}

.modal-wrapper {
  display: table-cell;
  vertical-align: middle;
}

.modal-container {
  width: 600px;
  margin: 0px auto;
  padding: 20px 30px;
  background-color: #fff;
  border-radius: 2px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
  transition: all 0.3s ease;
  font-family: Helvetica, Arial, sans-serif;
}

.modal-header h3 {
  margin-top: 0;
  color: #42b983;
}

.modal-body {
  margin: 20px 0;
}

/*
 * The following styles are auto-applied to elements with
 * transition="modal" when their visibility is toggled
 * by Vue.js.
 *
 * You can easily play with the modal transition by editing
 * these styles.
 */

.modal-enter {
  opacity: 0;
}

.modal-leave-active {
  opacity: 0;
}

.modal-enter .modal-container,
.modal-leave-active .modal-container {
  -webkit-transform: scale(1.1);
  transform: scale(1.1);
}
</style>