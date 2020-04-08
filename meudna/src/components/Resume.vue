<template>
  <div class="resume">
    <h2 class="resume__title"> {{ title }} </h2>
    <a href="https://www.linkedin.com/in/ihenrique/" class="resume__link" rel="author" target="_blank"> Ivan Henrique </a>
  </div>
</template>

<script>

export default {
  props: {
    title: {
      type: String,
      required: true
    },
  }
}
</script>
<style lang="scss">

</style>
