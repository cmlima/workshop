<template>
    <div class="galeria">
      <img v-for="(foto, index) in fotos" :key="`f-${index}`" :src="foto" class="galeria-imagem" :alt="`foto ${index}`">
    </div>
</template>

<script>

export default {
  props: {
    fotos: {
        type: Array,
        default: () => []
    }
  }
}
</script>

<style>
.galeria {
  line-height: 0;
  column-count: 4;
  column-gap: 0px;
  max-height: 480px;
  max-width: 96vw;
  overflow: hidden;
}
.galeria-imagem {
  width: 24vw !important;
  height: 220px !important;
  object-fit: cover;
}

@media (max-width: 800px) {
  .galeria {
    -moz-column-count: 2;
    -webkit-column-count: 2;
    column-count: 2;
  } 
}

@media (max-width: 400px) {
  .galeria {
    -moz-column-count: 1;
    -webkit-column-count: 1;
    column-count: 1;
  }  
}

</style>