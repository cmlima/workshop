<template>
  <footer>
    <img class="mb-4" :src="logo" height="60" alt="">
    <h6 class="h6">{{ titulo }}</h6>
    <p>{{ subtitulo }}</p>
    <small class="mt-5">{{ endereco }}</small>
    <small class="mt-4">Copyright © {{ `${new Date().getFullYear()} ${copyright}` }}</small>
  </footer>    
</template>

<script>
export default {
  props: {
    logo: {
      type: String,
      default: ''
    },
    titulo: {
      type: String,
      default: ''
    },
    subtitulo: {
      type: String,
      default: ''
    },
    endereco: {
      type: String,
      default: ''
    },
    copyright: {
      type: String,
      default: ''
    }
  }
}
</script>


<style>
footer {
  width: 100%;
  height: auto;
  padding: 5em 3em;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
}

footer p {
  font-size: 1rem;
}

</style>