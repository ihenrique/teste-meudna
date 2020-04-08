<template>
  <footer class="footer">
    <div class="footer__limit">
      <div class="footer__col">
        <slot name="column-A"></slot>
      </div>
      <div class="footer__col">
        <slot name="column-B"></slot>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'Footer',
  props: {
    
  }
}
</script>
<style lang="scss">

</style>
