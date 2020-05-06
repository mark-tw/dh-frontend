<template lang="pug">
.followers-condition
  .circle
  .followers-condition__title Conditions



</template>

<script lang="ts">
import { Vue, Component } from 'vue-property-decorator'

@Component({})
export default class FollowersCondition extends Vue {
}
</script>

<style lang="sass" scoped>
  .followers-condition
    display: flex
    align-items: center
    justify-content: flex-start
    background-color: #FF7629
    border: 1px solid #FF7629
    border-radius: 5px
    height: 36px
    &__title
      color: #FFFFFF
      font-style: normal
      font-weight: 500
      font-size: 12px
      line-height: 14px
      cursor: default
  .circle
    width: 6px
    height: 6px
    border: solid #FF7629 2px
    border-radius: 10px
    background-color: white
    transform: translateX(-5px)
</style>
