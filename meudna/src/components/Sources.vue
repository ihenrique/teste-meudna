<template>
  <div class="sources">
      <h2 class="sources__title"> {{ title }} </h2>
      <ul class="sources__list">
          <li class="source" v-for="source in sources_list" :key="source.title">
              <Source :title="source.title" :desc="source.desc" :links="source.links" />
          </li>
      </ul>
  </div>
</template>

<script>
import Source from '@/components/Source.vue';

export default {
  name: 'Sources',
  props: {
    title: {
      type: String,
      required: true
    },
    sources_list: {
      type: Array,
      required: true
    },
  },
  components: {
    Source
  }
}
</script>
<style lang="scss">

</style>
