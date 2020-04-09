<template>
  <div class="resume">
    <h2 class="resume__title"> {{ title }} </h2>
    <p class="resume__desc"> Teste desenvolvido por <a href="https://www.linkedin.com/in/ihenrique/" class="resume__link" rel="author" target="_blank"> Ivan Henrique </a> para a vaga de front-end. </p>
    
  </div>
</template>

<script>

export default {
  name: 'Resume',
  props: {
    title: {
      type: String,
      required: true
    },
  }
}
</script>
<style lang="scss">
.resume__title{
  @extend %h2;
}

.resume__desc{
  display: block;
}
</style>
