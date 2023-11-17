<script>
import AppHeader from './views/Shop/components/Header.vue';
import Home from './views/Home.vue';
import About from './views/About.vue';
import Contacts from './views/Contacts.vue';
import Cart from './views/Cart.vue';
import Shop from './views/Shop/components/Shop.vue';
import AppFooter from './views/Shop/components/Footer.vue';
export default {
  components: {
    AppHeader,
    Home,
    About,
    Contacts,
    Cart,
    Shop,
    AppFooter,
  },
  data() {
    return {
      view: 'Home'
    }
  },
  methods:{
    onNavSelect(selectedView){
      this.view = selectedView
    }
  },
};
</script>

<template>
  <AppHeader @on-select="onNavSelect"/>
  <!-- <ComponentsStarter /> -->
  <main>
    <component :is="view"/>
  </main>
  <AppFooter/>
</template>

<style scoped>
main {
  padding: 1rem 2rem;
}
</style>