<template>
  <b-container class="main-container d-flex flex-column align-items-center justify-content-center">
    <b-row>
      <b-col>
        <h1 class="display-2">404</h1>        
      </b-col>
    </b-row>
    <b-row>
      <b-col>
        <h4 class="lead">
          Como você veio parar aqui?
        </h4>
      </b-col>
    </b-row>
    <b-row>
      <NuxtLink to="/">
        Home page
      </NuxtLink>
    </b-row>
  </b-container>
</template>

<script>
export default {
  layout: 'empty'
}
</script>
