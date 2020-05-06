<template lang="pug">
.followers-table-inputs
  .input-block
    base-input(
      v-for="(elements, index) in elements"
      :key="index"
      :index="index"
      :value="elements.condition.value"
      @remove-element="removeElement"
      @input="changeConditionValue"
    )
  .add-value-button(
    @click="addValue"
  ) + Add value
  .circle

</template>

<script lang="ts">
  import { Vue, Component, Prop } from 'vue-property-decorator'
  import { _Element } from '@/components/utils'
  import BaseInput from '@/components/base/inputs/BaseInput.vue'

@Component({
  components: {BaseInput}
})
export default class FollowersTableInputs extends Vue {
  @Prop({default: () => []})
  elements!: _Element[]

  get lastElement (): _Element {
    return this.elements[this.elements.length -1]
  }

  addValue () {
    const newValue = JSON.parse(JSON.stringify(this.lastElement))
    this.lastElement.onFail = { action:"fallthrough" }
    this.elements.push(newValue)

  }
  changeConditionValue (input: { index: number, value: number}) {
    const i = input.index

    Vue.set(this.elements[i].condition, 'value', input.value)
    console.log(this.elements)
  }


  removeElement (index: number) {
    return this.elements.splice(index, 1)
  }
}
</script>

<style lang="sass" scoped>
  .add-value-button
    color: #6DD230
    padding-left: 12px
    font-size: 12px
    line-height: 14px
    cursor: pointer

  .circle
    width: 6px
    height: 6px
    border: solid #FF7629 2px
    border-radius: 10px
    background-color: white
    transform: translateX(87px) translateY(-12px)
</style>
