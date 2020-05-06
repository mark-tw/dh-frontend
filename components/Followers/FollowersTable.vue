<template lang="pug">
.followers-table
  .followers-table-main-block
    .followers-table-info
      .compare-followers-count Followers count
      .distinction is &nbsp;
        base-dropdown(
          :values="items"
          :defaultValue="defaultValue"
          @select="selectedValue"
        )
        span &nbsp; than
  .followers-table-inputs
    followers-table-inputs(
      :elements="elements"
    )



</template>

<script lang="ts">
import { Vue, Component, Prop } from 'vue-property-decorator'
import { _Element } from '../utils'
import BaseDropdown from '@/components/base/dropdowns/BaseDropdown.vue'
import FollowersTableInputs from '@/components/Followers/FollowersTableInputs.vue'



@Component({
  components: {FollowersTableInputs, BaseDropdown}
})
export default class FollowersTable extends Vue {
  @Prop({default: () => []})
  elements!: _Element[]

  items: string[] = ['Greater', 'Less']
  defaultValue: string = 'Greater'

  selectedValue (value: string) {
    this.defaultValue = value
    this.$emit('select', value)
  }


}

</script>

<style lang="sass" scoped>
.followers-table
  display: flex
  border-bottom: 1px dashed #E8ECEF
  border-top: 1px solid #F2F4F6

.followers-table-main-block
  width: 154px
  border-right: 1px dashed #E8ECEF

.compare-followers-count, span
  cursor: default
.distinction
  display: flex
  cursor: default
.followers-table-info
  padding: 13px 12px

.followers-table-inputs
  width: 92px

</style>
