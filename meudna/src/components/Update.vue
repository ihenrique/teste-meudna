<template>
  <div :class=" 'update' + ( compact ? '--compact' : '' ) ">
    <template v-if="compact">
      <h2 class="update__title"> {{ title }} </h2>
      <time class="update__date" datetime="2008-02-14 20:00">
          {{ last_updated }}
      </time>
    </template>
    <template v-else>
      <h2 class="update__title"> {{ title }} </h2>
      <p class="update__info">
          <time class="update__date" datetime="2008-02-14 20:00">
              {{ formated_date }}
          </time>
          <span class="update__alert">
            <div class="icon">
              <svg xmlns="http://www.w3.org/2000/svg" aria-hidden="true" focusable="false" role="img" viewBox="0 0 512 512"><path fill="currentColor" d="M504 256c0 136.997-111.043 248-248 248S8 392.997 8 256C8 119.083 119.043 8 256 8s248 111.083 248 248zm-248 50c-25.405 0-46 20.595-46 46s20.595 46 46 46 46-20.595 46-46-20.595-46-46-46zm-43.673-165.346l7.418 136c.347 6.364 5.609 11.346 11.982 11.346h48.546c6.373 0 11.635-4.982 11.982-11.346l7.418-136c.375-6.874-5.098-12.654-11.982-12.654h-63.383c-6.884 0-12.356 5.78-11.981 12.654z"/></svg>
            </div>
              {{ alert }}
          </span>
      </p>
    </template>
  </div>
</template>

<script>

export default {
  name: 'Update',
  props: {
    compact: {
      type: Boolean,
    },
    title: {
      type: String,
      required: true
    },
    date: {
      type: Number,
    },
    alert: {
      type: String,
    }
  },
computed: {
    formated_date: function () {
      var _date = new Date( this.date );

      return `${("0" + _date.getDate()).slice(-2)}/${("0" + (_date.getMonth() + 1)).slice(-2)}/${_date.getFullYear()} às ${("0" + _date.getHours()).slice(-2)}:${("0" + _date.getMinutes()).slice(-2)}:${("0" + _date.getSeconds()).slice(-2)}`;
    },
    last_updated: function () {
      var _now = new Date().getTime();

      return `${ Math.round( ( _now - this.date ) / 60000 ) } minutos`
    },
  }
}
</script>
<style lang="scss">
.update__title{
  @extend %h2;
}

.update__date{
  display: block;
  margin-bottom: .3rem;
}

.update__alert{
  font-size: .8rem;
  color: $damask;

  .icon{
    @extend %icon;
  }
}

.update--compact{
  display: inline-block;
  padding: .5rem;
  border-radius: 8px;
  background-color: $bluewood;
  box-shadow: 0 2px 5px rgba(255, 255, 255, 0.4);

  .update__title,
  .update__date{
    display: inline;
  }
  
  .update__date{
    font-weight: 500;
    color: $cream;
    margin-bottom: 0;
  }
}
</style>
