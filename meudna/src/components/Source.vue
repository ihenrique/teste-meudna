<template>
  <div class="source">
      <p class="source__name">
        <b class="source__title"> {{ title }} </b>
        {{ desc }}
      </p>
      <a class="souce__link"  :href="link.url" v-for="link in links" :key="link.name" target="_blank">
          {{ link.name }}
          <i class="icon">
            <svg aria-hidden="true" focusable="false" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"><path fill="#efc958" d="M432,320H400a16,16,0,0,0-16,16V448H64V128H208a16,16,0,0,0,16-16V80a16,16,0,0,0-16-16H48A48,48,0,0,0,0,112V464a48,48,0,0,0,48,48H400a48,48,0,0,0,48-48V336A16,16,0,0,0,432,320ZM488,0h-128c-21.37,0-32.05,25.91-17,41l35.73,35.73L135,320.37a24,24,0,0,0,0,34L157.67,377a24,24,0,0,0,34,0L435.28,133.32,471,169c15,15,41,4.5,41-17V24A24,24,0,0,0,488,0Z"></path></svg>
          </i>
      </a>
  </div>
</template>

<script>

export default {
  name: 'Source',
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
.source{
  padding: 1rem;
  border: 1px solid #fff;
  border-radius: 5px;
  line-height: 1.5;
}

.source__title{
  display: block;
  color: $cream;
}

.souce__link{
  display: block;

  .icon{
    @extend %icon;
  }
}
</style>
