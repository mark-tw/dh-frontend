<template lang="pug">
.followers-block
  followers-condition
  .followers-table__title-block
    .followers-table__icon
      img(src="@/assets/img/arrow.svg")
    .followers-table__title Followers
  followers-table(
    :elements="data.elements"
    @select="changeFooterDifference"
  )
  .followers-table-footer
    .followers-count Followers count is
    .followers-value {{this.difference}} {{countValue}}
    .circle



</template>

<script lang="ts">
import { Vue, Component, Prop } from 'vue-property-decorator'
import { mockJSON, _Element} from '@/components/utils'
import FollowersCondition from '@/components/Followers/FollowersCondition.vue'
import FollowersTable from '@/components/Followers/FollowersTable.vue'

@Component({
  components: {FollowersTable, FollowersCondition}
})
export default class FollowersBlock extends Vue {
  @Prop({default: () => ({})})  data!: mockJSON

  difference: string = '<'
  changeFooterDifference (value:string) {
    value === 'Greater'
      ? this.difference = '<'
      : this.difference = '>'
  }
  get countValue () {
    return this.data.elements[0].condition.value
  }

}

</script>

<style lang="sass" scoped>
  .followers-table__title-block
    display: flex
    height: 32px
    align-items: center
    cursor: default

  .followers-table-title
    color: #778CA2
    font-size: 10px
    line-height: 12px

  .followers-table-footer
    display: flex
    height: 40px
    align-items: center

  .followers-count
    color: #778CA2
    padding-left: 12px
    width: 130px
    height: 14px
    padding-right: 24px
    cursor: default

  .followers-value
    color: #FF4550
    cursor: default

  .followers-table__icon
    padding: 12px 5px

  .circle
    width: 6px
    height: 6px
    border: solid #FF7629 2px
    border-radius: 10px
    background-color: white
    transform: translateX(37px)
</style>
