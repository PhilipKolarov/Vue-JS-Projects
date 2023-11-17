<script>
import Card from './components/Card.vue';

export default {
    data() {
        return {
            cards: [
                {idx: 0, type: "Vue", img: "https://upload.wikimedia.org/wikipedia/commons/thumb/9/95/Vue.js_Logo_2.svg/2367px-Vue.js_Logo_2.svg.png"},
                {idx: 1, type: "Vue", img: "https://upload.wikimedia.org/wikipedia/commons/thumb/9/95/Vue.js_Logo_2.svg/2367px-Vue.js_Logo_2.svg.png"},
                {idx: 2, type: "React", img: "https://upload.wikimedia.org/wikipedia/commons/thumb/a/a7/React-icon.svg/1150px-React-icon.svg.png"},
                {idx: 3, type: "React", img: "https://upload.wikimedia.org/wikipedia/commons/thumb/a/a7/React-icon.svg/1150px-React-icon.svg.png"},
            ],
            selectedItems: [],
            guessedItems: []
        }
    },
    methods: {
        handleSelect(idx, type) {
            if (this.selectedItems.length < 2) {
                this.selectedItems.push({ idx, type });
            }
            else if(this.selectedItems.length === 2) {
                this.selectedItems = [{idx, type}];
            }
        }
    },
    watch: {
        selectedItems: {
            handler(newVal) {
                if(newVal.length === 2 && newVal[0].type == newVal[1].type)
                    this.selectedItems.push(newVal[0].type);
            },
            deep: true
        }
    },
    components: {
        Card
    }
}
</script>

<template>
    <h1>MY FLIP GAME</h1>
    <div class="myGrid">
        <Card
          v-for="card in cards" 
          :key="card.idx" 
          :idx="card.idx"
          :img="card.img"
          :type="card.type"
          :active-items="selectedItems"
          :on-click="handleSelect"
          :guessed-items="guessedItems"/>
    </div>
</template>

<style scoped>
h1 {
    display: flex;
    margin-top: 20px;
    margin-bottom: 20px;
    margin-left: 42%;
}

.myGrid {
    max-width: 400px;
    margin: 0 auto;
    display: grid;
    grid-template-columns: repeat(2, minmax(50px, 1fr));
    gap: 1rem;
}
</style>