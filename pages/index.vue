<template>
  <div class="scroll-container">
    <section
      v-for="(secao, index) in secoes"
      :key="`s-${index}`"
      class="container-secao"
      :style="getBackgroundStyle(secao)"
    >
      <div 
        class="conteudo-sessao d-flex flex-column align-items-center justify-content-center" 
        :class="{ overlay: secao.overlay, 'pagina-inteira': secao.paginaInteira }">

        <nuxt-content :document="secao" />

        <div v-if="secao.paginaInteira && index < secoes.length - 1" class="container-seta pa-4">
          <svg class="seta" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3" />
          </svg>          
        </div> 

      </div>
    </section>
  </div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    const secoes = await $content('secoes').sortBy('ordem').fetch();
    return { secoes };
  },
  methods: {
    getBackgroundStyle(secao) {
      const image = secao.background;
      const color = secao.backgroundColor;
      return {
        backgroundColor: color || 'transparent',
        backgroundImage: image ? `url(${image})` : '',
        backgroundRepeat: 'no-repeat',
        backgroundPosition: 'center center',
        backgroundSize: 'cover'
      }
    }
  }
}
</script>

<style>
.scroll-container {
  height: 100vh;
  overflow-y: scroll;
  overflow-x: hidden;
  scroll-snap-type: mandatory;
  scroll-snap-type: y mandatory;
}
.container-secao {
  scroll-snap-align: start;
}

.conteudo-sessao {
  max-width: 100%;
  position: relative;
}

.pagina-inteira {
  min-height: 100vh;
}

.overlay {
  background-color: rgba(0, 0, 0, 0.6);
}

.container-seta {
  width: 80px;
  height: 80px;
  position: absolute;
  bottom: 0;
}

.seta {
  stroke: lightgray;
  width: 60px;
  height: 60px;
  animation: bounce 1s infinite alternate;
}

@keyframes bounce {
  from {
    margin-top: 0;
  }
  to {
    margin-top: -15px;
  }
}
</style>
