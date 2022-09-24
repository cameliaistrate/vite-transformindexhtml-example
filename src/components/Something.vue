<template>
  <div class="test">Something, something</div>  
  <!-- <slot name="namedSlot" v-bind:customData="customDataInChild" /> -->
  <slot name="namedSlot" v-bind:customData="{customTitle: customTitle, someValue: someValue}" />
  <template>
  <!-- <div class="test"> -->
    <slot name="otherSlot"></slot> <!--  works inside div, but not inside template? -->
  <!-- </div> -->    
  </template>
</template>

<script>

export default {
  data () {
    return {
      /* customDataInChild: {
        customTitle: 'My Custom Title',
        someValue: 5
      } */
      customTitle: 'My Custom Title',
      someValue: 5
    }
  }
};
</script>

<style lang="sass" scoped>

</style>

