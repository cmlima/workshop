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
        :class="{ overlay: secao.overlay }">

        <nuxt-content :document="secao" />

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
      const imageUrl = secao['background-image'];
      const color = secao['background-color'];
      return {
        backgroundColor: color || 'transparent',
        backgroundImage: imageUrl ? `url('${imageUrl}')` : '',
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
  overflow: scroll;
  scroll-snap-type: mandatory;
  scroll-snap-type: y mandatory;
}
.container-secao {
  scroll-snap-align: start;
  min-height: 100vh;
  min-width: 100vw;
}

.conteudo-sessao {
  min-height: 100vh;
  min-width: 100vw;
}

.overlay {
  background-color: rgba(0, 0, 0, 0.6);
}
</style>
