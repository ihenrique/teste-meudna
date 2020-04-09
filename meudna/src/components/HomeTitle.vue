<template>
  <h1 class="hometitle">
      {{ hat }}
      <span class="hometitle__title"> {{ title }} </span>
      <span class="hometitle__sub"> {{ subtitle }} </span>
  </h1>
</template>

<script>

export default {
  name: 'HomeTitle',
  props: {
    title: {
    type: String,
      required: true
    },
    subtitle:{
      type: String,
    },
    hat:{
      type: String,
    }
  }
}
</script>
<style lang="scss">

  .hometitle{
    font-size: 1.2rem;
    line-height: 1;
    text-transform: uppercase;
    text-align: center;
    font-weight: bold;
    color: $blueocean;

    @media screen and ( min-width: 520px ){
      font-size: 1.5rem;
    }
  }

  .hometitle__title{
    display: block;
    font-size: 2.8rem;
    line-height: 1.2;
    color: $white;

    @media screen and ( min-width: 520px ){
      font-size: 3.5rem;
    }
  }

  .hometitle__sub{
    color: $cream;
  }

</style>
