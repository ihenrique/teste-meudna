<template>
  <div class="source">
      <p class="source__name">
        <b class="source__title"> {{ title }} </b>
        {{ desc }}
      </p>
      <a :href="link.url" class="souce__link" v-for="link in links" :key="link.name">
          {{ link.name }}
      </a>
  </div>
</template>

<script>

export default {
  props: {
    title: {
      type: String,
      required: true
    },
    desc: {
      type: String
    },
    links: {
      type: Array
    }
  }
}
</script>
<style lang="scss">

</style>
