<template>
  <div>
    <div
      class="equipe d-flex align-items-center justify-content-center"
    >
      <h1 class="display-1 text-center">{{ equipe.nome }}</h1>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params, error }) {
    let equipe;
    try {
      equipe = await $content('equipes', params.slug).fetch();
    } catch (e) {
      return error({ statusCode: 404 })
    }
    if (!equipe || !params.slug) {
      return error({ statusCode: 404 })
    }
    return { equipe };
  }
}
</script>

<style>
.equipe {
  min-height: 100vh;
  min-width: 100vw;
}
</style>
