<template>
  <div>
    <div
      v-for="(secao, index) in secoes"
      :key="`s-${index}`"
      class="secao d-flex align-items-center justify-content-center"
      :style="{ backgroundColor: secao['background-color']}"
    >
      <h1 class="display-1">{{ secao.nome }}</h1>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    const secoes = await $content('secoes').sortBy('ordem').fetch();
    return { secoes };
  }
}
</script>

<style>
.secao {
  min-height: 100vh;
  min-width: 100vw;
}
</style>
