<template>
  <div id="app">
    <transition name="page-view">
      <component :is="view.page" @back="onBack" @finished="onStepFinished"></component>
    </transition>
  </div>
</template>

<script>
import { mapState, mapMutations } from 'vuex'
import ManagePanel from './views/ManagePanel'
import Options from './views/Options'
import Feature from './views/Feature'
import Setup from './views/Setup'

export default {
  name: 'ussr',
  components: { Feature, Setup, ManagePanel, Options },
  computed: {
    ...mapState(['view']),
  },
  methods: {
    ...mapMutations(['prevView', 'nextView']),
    onBack () {
      this.prevView()
    },
    onStepFinished () {
      this.nextView()
    },
  },
}
</script>

<style lang="stylus">
@import './assets/styles'
@import './assets/base.styl'
</style>
