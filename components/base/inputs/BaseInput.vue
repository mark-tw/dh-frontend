<template lang="pug">
  .base-input
    .delete-icon(
      v-if="index"
      @click="removeElement"
    )
      img(src="@/assets/img/cross.png")
    input(
    v-model="inputValue"
    )
    .dashed-border
    .circle

</template>

<script lang="ts">
import { Component, Vue, Prop } from 'vue-property-decorator'

@Component({})
export default class BaseInput extends Vue {

  @Prop() value!: number
  @Prop({default: 0}) index!: number

  get inputValue (): number {
    return this.value
  }

  set inputValue (value :number) {
    const {index} = this

    this.$emit('input', {
      index,
      value
    })
  }
  removeElement () {
    this.$emit('remove-element', this.index)

  }
}
</script>

<style lang="sass" scoped>
.delete-icon
  opacity: 0
  position: absolute
  transform: translateY(72%) translateX(-2px)
  cursor: pointer
  &:hover
    opacity: 1
img
  width: 15px
  height: 15px
  color: black
input
  display: block
  font-family: 'Rubik'
  outline: none
  text-align: right
  border: none
  width: 40px
  padding: 13px 0 12px 12px

.dashed-border
  border-bottom: 1px dashed #E8ECEF

.circle
  width: 6px
  height: 6px
  border: solid #FF7629 2px
  border-radius: 10px
  background-color: white
  transform:  translateX(87px) translateY(-26px)
</style>
