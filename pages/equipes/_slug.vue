<template>
    <div
      class="scroll-container p-5"
    >
      <nuxt-content class="conteudo" :document="equipe" />
    </div>
</template>

<script>
export default {
  async asyncData({ $content, params, error }) {
    let equipe;
    equipe = await $content('equipes', params.slug)
      .fetch()
      .catch((err) => {
        return error({ statusCode: 404 })
      });
    if (!equipe || !params.slug) {
      return error({ statusCode: 404 })
    }
    return { equipe };
  }
}
</script>

<style>

.scroll-container {
  height: 100vh;
  overflow-y: scroll;
  overflow-x: hidden;
}

.conteudo {
  height: 100%;
}

</style>
