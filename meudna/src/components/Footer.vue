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
.footer{
  border-top: 1px solid lighten( $bluewood , 10 );

  .update{
    margin-bottom: 2rem;
  }
}

.footer__limit{
  @extend %limit;

  @media screen and ( min-width: 640px ){
    display: flex;
    justify-content: space-between;
  }
}

.footer__col{
  width: 100%;

  @media screen and ( min-width: 640px ){
    width: calc( 50% - 1rem );
  }
}
</style>
