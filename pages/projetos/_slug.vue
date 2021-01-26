<template>
  <div
    class="scroll-container p-5"
  >
    <nuxt-content class="conteudo" :document="projeto" />
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params, error }) {
    let projeto;
    projeto = await $content('projetos', params.slug)
      .fetch()
      .catch((err) => {
        return error({ statusCode: 404 })
      });
    if (!projeto || !params.slug) {
      return error({ statusCode: 404 })
    }
    return { projeto };
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
