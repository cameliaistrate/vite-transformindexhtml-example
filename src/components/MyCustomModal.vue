<template>
  <div class="modal">
    <h2>MODAL TITLE</h2>
    <slot></slot>
    <button @click="emitClose">CLOSE ME</button>
  </div>
</template>

<script>
export default {
  methods: {
    emitClose () {
      this.$emit('close')
    }
  }
}
</script>

<style lang="sass" scoped>
.modal
  position: fixed
  z-index: 999
  top: 0
  left: 0
  width: 100%
  height: 100%
  background-color: rgba(235, 235, 241, 0.5)
  display: flex
  flex-direction: column
  justify-content: center
  align-items: center
</style>