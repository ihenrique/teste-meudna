<template>
  <div class="update">
    <h2 class="update__title"> {{ title }} </h2>
    <p class="update__info">
        <time class="update__date" datetime="2008-02-14 20:00">
            {{ date }}
        </time>
        <span class="update__alert">
            {{ alert }}
        </span>
    </p>
  </div>
</template>

<script>

export default {
  props: {
    title: {
      type: String,
      required: true
    },
    date: {
      type: Number,
      required: true
    },
    alert: {
      type: String,
    }
  }
}
</script>
<style lang="scss">

</style>
