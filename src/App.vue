<template>
  <div class="main">
    <HelloWorld msg="Hello Vue 3 + Vite" @themeColorChange="changeBackground">
      <!-- all this will go into default slot... -->
      <p>Fill HelloWorld slot from parent w/ vue3 slot syntax:</p>
      <div class="slot-test">
        <p>Hello From Parent Component, I'm a <code>p</code> tag!</p>
        <p>placed into the child's slot</p>
      </div>
      <!-- ...up until this point. -->
      <!-- This will go into the named slot: -->
      <div class="named-slot-test">
        <!-- <Something slot="namedSlot" /> -->
        <Something #namedSlot />
        <!-- could be: <Something v-slot:namedSlot /> -->
      </div>
      <div class="named-slot-test named-slot-test-variables">
        <!-- now add some variables, too: -->
        <!-- <Something #namedSlot="slotProps"> -->
        <Something v-slot:namedSlot="slotProps">
          <p>title: {{ slotProps.customData.customTitle }}</p>
          <p>someValue: {{ slotProps.customData.someValue }}</p> 
        </Something>
      </div>
      <Something>
        <template #otherSlot>
          <div>are we here?</div>
        </template>
      </Something>
    </HelloWorld>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';
import Something from './components/Something.vue';

export default {
  components: {
    HelloWorld,
    Something,
  },

  data() {
    return {
      siteBackground: 'darkgreen',
    };
  },

  methods: {
    changeBackground(value) {
      console.log(value);
      this.siteBackground = value;
    },
  },
};
</script>

<style>
body {
  margin: 0;
  height: 100%;
  width: 100%;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 0;
}

.main {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding-top: 60px;
  box-sizing: border-box;
  background: linear-gradient(
    135deg,
    rgba(240, 255, 255, 1) 35%,
    v-bind('siteBackground') 100%
  );
  height: 100%;
  width: 100%;
}

.slot-test {
  border: 2px dashed #d2d2d2;
  padding: 0 6px;
}

.named-slot-test {
  border: 2px dashed darkblue;
  padding: 0 6px;
  margin-top: 12px;
}
</style>
