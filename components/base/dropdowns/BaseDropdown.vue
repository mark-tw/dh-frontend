<template lang="pug">
.base-dropdown
  .base-dropdown__select(
    @click="openDropdown"
  )
    .base-dropdown__value {{defaultValue}}
    .base-dropdown__arrow(
      :class="{active: isVisible}"
    )
      img(src="@/assets/img/open-close-dropdown.svg")
  transition(name="fade")
    .base-dropdown__menu(
      v-if="isVisible"
    )
      .base-dropdown__options(
        v-for="value in values"
        @click="selectedValue(value)"
      ) {{value}}

</template>

<script lang="ts">
import { Vue, Component, Prop } from 'vue-property-decorator'



@Component({})
export default class BaseDropdown extends Vue {
  @Prop({default: () => []}) values!: string[]
  @Prop() defaultValue!: string

  isVisible: boolean = false

  openDropdown () {
    this.isVisible = !this.isVisible
  }

  selectedValue (value: string) {
    this.isVisible = false
    this.$emit('select', value)
  }
}
</script>

<style lang="sass" scoped>
.base-dropdown
  cursor: pointer
  &__select
    display: flex
  &__value
    font-weight: bold
    color: black
  &__arrow
    padding-left: 2px
    transition: all .6s ease-in-out
    &.active
      transform: scale(1, -1)
      transition: all .6s ease-in-out
  &__menu
    display: flex
    position: absolute
    transform: translateX(28px)
    flex-direction: column
  .fade-enter-active, .fade-leave-active
    transition: opacity .5s

  .fade-enter, .fade-leave-to
    opacity: 0

  &__options
    background-color: white
    border: solid 1px #F2F4F6
    padding: 5px
    cursor: pointer
    &:hover
      background-color: #F2F4F6
</style>
