<script>
import { computed } from '@vue/reactivity';
import { emit } from 'process';


export default {
  props: {
    img:{
      type: String,
      required: true
    },
    type:{
      type: String,
      required: true
    },
    idx:{
      type: String,
      required: true
    },
    activeItems: {
      type: Array
    },
    guessedItems: {
      type: Array
    }
  },
  emits:['onClick'],
  computed: {
    isActive() {
      if (!this.activeItems.length) 
        return false;

      const idxs = this.activeItems.map(i => i.idx);
      return this.guessedItems.includes(this.type) || idxs.includes(this.idx);
    },
  },
  methods:{
    onSelect(){
      if(!this.isActive) {
        this.$emit('onClick', this.idx, this.type);
      }
    }
  }
  
};
</script>

<template>
  <article class="card" @click="$emit('onClick', idx, type)">
    <template v-if="isActive">
      <img :src="img" alt="Logo">
      <h2>{{ type }}</h2>
    </template>
    <img v-else src="https://upload.wikimedia.org/wikipedia/commons/thumb/3/30/Card_back_05a.svg/1200px-Card_back_05a.svg.png" alt="back-of-card">
  </article>
</template>

<style scoped>
.card {
  margin: 0;
  text-align: center;
  padding: 12px;
}
</style>
