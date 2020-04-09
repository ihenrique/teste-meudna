<template>
  <figure :class=" 'case' + ( color ? ' -is-' + color : '' ) ">
    <p class="case__numbers"> {{ number }} </p>
    <figcaption class="case__legend">
      {{ legend }}
    </figcaption>
  </figure>
</template>

<script>

export default {
    name: 'Case',
    props: {
        number: {
            type: Number,
            required: true
        },
        legend: {
            type: String,
        },
        color: {
            type: String,
        }
    }
}
</script>
<style lang="scss">
.case{
  display: inline-block;
  text-align: center;

  &.-is-red{
    .case__numbers{
      color: $amared;
    }

    .case__legend{
      color: $white;
      background-color: $amared;
    }
  }

  &.-is-blue{
    .case__numbers{
      color: $blueocean;
    }

    .case__legend{
      color: $white;
      background-color: $blueocean;
    }
  }
}


.case__numbers{
  font-size: 4rem;
  font-weight: bold;
  letter-spacing: 1px;
  color: $cream;
  line-height: 1;

  @media screen and ( min-width: 520px ){
    font-size: 6rem;
  }
}

.case__legend{
  display: inline-block;
  color: $bluewood;
  background-color: $cream;
  font-size: 1rem;
  font-weight: 500;
  padding: 6px;
  border-radius: 4px;
  box-sizing: border-box;
}
</style>
