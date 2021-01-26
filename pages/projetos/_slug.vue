<template>
  <div>
    <div
      class="projeto d-flex align-items-center justify-content-center"
    >
      <h1 class="display-1">{{ projeto.titulo }}</h1>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params, error }) {
    try {
      const projeto = await $content('projetos', params.slug).fetch();
    } catch (e) {
      return error({ statusCode: 404 })
    }
    return { projeto };
  }
}
</script>

<style>
.projeto {
  min-height: 100vh;
  min-width: 100vw;
}
</style>
