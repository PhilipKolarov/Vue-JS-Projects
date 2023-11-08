<script>
  export default {
    data() {
      return {
        count: 0,
        user: {
          name: 'Philp',
          hobby: 'Bass'
        },
      };
    },
    mounted() {
      console.log('My name is', this.user.name);
      this.changeMyName();
      console.log('My name is', this.user.name);
    },
    methods: {
      changeMyName(){
        this.user.name = 'Phil'
      },
      changeMyHobby(){
        this.user.hobby = 'None'
      }
    },
  };
</script>

<template>
  <div>
    'Hello world!'
  </div>
</template>

<style lang="scss" scoped>

</style>
