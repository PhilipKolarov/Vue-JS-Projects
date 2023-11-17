<script>
import {categories} from "../../../constants/categories.js"
    export default {
        data() {
            return {
                categories
            }
        },
        props:{
            activeItem:{
                type: String,
                required: true
            }
        },
        emits:['onSelect'],
        methods:{
            onSelect(selected){
                if(this.activeItem === selected) {
                    this.$emit('onSelect', '')
                }
                else {
                    this.$emit('onSelect', selected)
                }
            }
        }
    }
</script>

<template>
    <div>
      <ul role="list" class="categories">
        <li v-for="cat in categories" :key="cat.value">
            <!-- class="primary" -->
          <button :class="[activeItem === cat.value ? 'primary' : 'secondary outline']" @click="onSelect(cat.value)">
            {{ cat.name }}
          </button>
        </li>
      </ul>
    </div>
</template>

<style scoped>
.categories {
  display: flex;
  justify-content: center;
  gap: 1rem;
}
</style>