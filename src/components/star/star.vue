<template>
  <div class="star" :class="starType">
    <span v-for="(itemClass,index) in itemClasses" :class="itemClass" class="star-item" key="index"></span>
  </div>
</template>

<script>
  export default {
    props: {
      size: {
        type: Number
      },
      score: {
        type: Number
      }
    },
    data () {
      return {
        LENGTH: 5,
        CLS_ON: 'on',
        CLS_HALF: 'half',
        CLS_OFF: 'off'
      };
    },
    computed: {
      starType () {
        return 'star-' + this.size;
      },
      itemClasses () {
        let result = [];
        let score = Math.floor(this.score * 2) / 2;
        let hasDecimal = score % 1 !== 0;
        let integer = Math.floor(score);
        for (let i = 0; i < integer; i++) {
          result.push(this.CLS_ON);
        }
        if (hasDecimal) {
          result.push(this.CLS_HALF);
        }
        while (result.length < this.LENGTH) {
          result.push(this.CLS_OFF);
        }
        return result;
      }
    }
  };
</script>

<style lang="sass">
  @import "../../common/sass/mixin"

  .star
    font-size: 0
    .star-item
      display: inline-block
      background-repeat: no-repeat
    &.star-48
      .star-item
        width: 20px
        height: 20px
        margin-right: 22px
        background-size: 20px 20px
        &:last-child
          margin-right: 0
        &.on
          @include image('star48_on')
        &.half
          @include image('star48_half')
        &.off
          @include image('star48_off')
    &.star-36
      .star-item
        width: 15px
        height: 15px
        margin-right: 6px
        background-size: 15px 15px
        &:last-child
          margin-right: 0
        &.on
          @include image('star36_on')
        &.half
          @include image('star36_half')
        &.off
          @include image('star36_off')
    &.star-24
      .star-item
        width: 10px
        height: 10px
        margin-right: 3px
        background-size: 10px 10px
        &:last-child
          margin-right: 0
        &.on
          @include image('star24_on')
        &.half
          @include image('star24_half')
        &.off
          @include image('star24_off')
</style>