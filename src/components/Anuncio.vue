<template>
  <div class="card">
    <img :src="imageUrl" class="card-img-top" alt="">
    <div class="card-body">
      <h5 class="card-title">$ {{ price }} MN</h5>
      <p class="text-small">{{ typeName }}</p>
      <p class="card-text">{{ title }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Anuncio',
  props: {
    title: String,
    price: Number,
    imageUrl: String,
    typeName: String
  }
}
</script>
