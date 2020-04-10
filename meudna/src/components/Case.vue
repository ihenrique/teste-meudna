<template>
  <figure :class=" 'case' + ( color ? ' -is-' + color : '' ) ">
    <template v-if="number">
      <p class="case__numbers"> {{ number }} </p>
    </template>
    <template v-else>
      <svg class="case__loader" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 44 44" stroke="#fff" >
          <g fill="none" fill-rule="evenodd" stroke-width="2">
              <circle cx="22" cy="22" r="19.3191">
                  <animate attributeName="r" begin="0s" dur="1.8s" values="1; 20" calcMode="spline" keyTimes="0; 1" keySplines="0.165, 0.84, 0.44, 1" repeatCount="indefinite"/>
                  <animate attributeName="stroke-opacity" begin="0s" dur="1.8s" values="1; 0" calcMode="spline" keyTimes="0; 1" keySplines="0.3, 0.61, 0.355, 1" repeatCount="indefinite"/>
              </circle>
              <circle cx="22" cy="22" r="10.3675">
                  <animate attributeName="r" begin="-0.9s" dur="1.8s" values="1; 20" calcMode="spline" keyTimes="0; 1" keySplines="0.165, 0.84, 0.44, 1" repeatCount="indefinite"/>
                  <animate attributeName="stroke-opacity" begin="-0.9s" dur="1.8s" values="1; 0" calcMode="spline" keyTimes="0; 1" keySplines="0.3, 0.61, 0.355, 1" repeatCount="indefinite"/>
              </circle>
          </g>
      </svg>
    </template>
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
            type: String,
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
  animation: 1s appear;

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

.case__loader{
  display: block;
  margin: auto;
  margin-bottom: 1rem;
  width: 4rem;
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


@keyframes appear {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
</style>
