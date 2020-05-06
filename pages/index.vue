<template lang="pug">
  .app
    .followers-block
      followers-block(
        :data="mockJSON"
      )
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'
import {mockJSON} from '@/components/utils'
import FollowersBlock from '@/components/Followers/FollowersBlock.vue'


@Component({
  components: {FollowersBlock}
})
export default class index extends Vue {
  mockJSON: mockJSON = mockJSON
}
</script>

<style lang="sass">
  @import url('https://fonts.googleapis.com/css2?family=Rubik:wght@400&display=swap')
  .app
    margin: 0 auto
    display: flex
    font-family: 'Rubik'
    color: #778CA2
    font-size: 12px
    max-width: 246px
    height: fit-content
    box-shadow: 0 6px 32px rgba(152, 169, 188, 0.24), 0 4px 8px rgba(119, 140, 162, 0.08)
  .followers-block
    width: 100%
    height: 100%
</style>

