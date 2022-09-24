<template>
  <h3>{{ msg }}</h3>

  <div class="color-scheme-select">
    <h3>Click on the square to choose a color scheme:</h3>
    <div
      class="selector"
      v-for="(color, index) in availableColors"
      :style="`background-color: ${color}`"
      @click="changeThemeColor(color)"
    ></div>
    <div>{{ color }}</div>
  </div>

  <div class="trigger-modal">
    <button @click="showModal">SHOW THE MODAL!</button>
    <Teleport to="body">
      <my-custom-modal @close="hideModal" v-if="displayModal">
        <p>Look, I am the modal content inside the slot!</p>
      </my-custom-modal>
    </Teleport>
  </div>

  <slot />
  
</template>

<script>
import MyCustomModal from './MyCustomModal.vue'

export default {
  components: {
    MyCustomModal
  },

  props: {
    msg: {
      type: String,
      default: '',
    },
  },

  data() {
    return {
      availableColors: ['darkgreen', 'midnightblue', 'cornflowerblue'],
      color: 'darkgreen',
      displayModal: false      
    };
  },

  methods: {
    changeThemeColor(col) {
      this.color = col;
      this.$emit('themeColorChange', col);
    },

    showModal () {
      this.displayModal = true
    },

    hideModal () {
      this.displayModal = false
    }
  },
};
</script>

<style lang="sass" scoped>
$section-top-margin: 30px

a
  color: v-bind(color) // #42b983

.selector
  display: inline-block
  width: 24px
  height: 24px
  margin-right: 12px
  cursor: pointer

.color-scheme-select
  margin-top: $section-top-margin

.trigger-modal
  margin-top: $section-top-margin

</style>

<!--<script setup>
import { ref } from 'vue';

defineProps({
  msg: String,
});

const count = ref(0);
</script>-->
