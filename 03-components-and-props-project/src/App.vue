<script>
import HelloWorld from './components/HelloWorld.vue';
import MyButton from './components/MyButton.vue';

export default {
  data() {
    return {
      btnColor: 'orange',
      countText: 0,
    };
  },
  components: {
    MyButton,
    HelloWorld
  },
  methods: {
    handleClick(count) {
      this.countText = count;
    },
  },
};
</script>

<template>
  <h1>Hello components</h1>
  <MyButton btnColor="red" @on-click="handleClick"></MyButton>
  <HelloWorld></HelloWorld>
</template>
