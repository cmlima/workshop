<template>
  <footer>
    <img class="mb-4" src="imagens/logos/jfsp.png" height="60" alt="">
    <h6 class="h6">UCIN - Subsecretaria de Comunicação, Conhecimento e Inovação</h6>
    <p>iJuspLab - Laboratório de Inovação da Justiça Federal de São Paulo</p>
    <small>Av. Paulista, 1682, 11º andar - Bela Vista, São Paulo/SP - CEP 01310-200</small>
    <small class="mt-4">Copyright © {{ new Date().getFullYear() + ' UCIN/iJuspLab' }}</small>
  </footer>    
</template>

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