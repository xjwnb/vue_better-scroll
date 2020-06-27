<template>
  <div class="wrapper" ref="wrapper">
    <div class="content">
      <slot></slot>
    </div>
  </div>
</template>

<script>
import BScroll from 'better-scroll'

export default {
  name: 'scroll',
  props: {
    probeType: {
      type: Number,
      default() {
        return 0
      }
    }
  },
  data() {
    return {
      scroll: null
    }
  },
  mounted() {
    this.scroll = new BScroll(this.$refs.wrapper, {
      click: true,
      probeType: this.probeType
    })

    if (this.probeType === 2 || this.probeType === 3) {
      this.scroll.on('scroll', position => {
        console.log(position)
        // console.log('---')
      })
    }
  },
  methods: {}
}
</script>

<style scoped>
</style>
