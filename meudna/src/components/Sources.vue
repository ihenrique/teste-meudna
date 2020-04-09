<template>
  <div class="sources">
      <h2 class="sources__title"> {{ title }} </h2>
      <ul class="sources__list">
          <li class="source__item" v-for="source in sources_list" :key="source.title">
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
.sources__title{
  @extend %h2;
}

.sources__list{
  list-style-type: none;

  @media screen and ( min-width: 1080px ){
    display: flex;
    justify-content: space-between;
  }
}

.source__item{

  @media screen and ( max-width: 1079px ){
    margin-bottom: 1rem;
  }

  @media screen and ( min-width: 1080px ){
    width: calc( 50% - 0.5rem );
  }
}
</style>
