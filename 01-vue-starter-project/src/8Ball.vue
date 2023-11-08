<script>
    export default {
        data(){
            return {
                isThinking:false,
                hasAnswer:false,
                answer: '',
                possibleAnswers: ['Yes', 'No', 'Maybe'],
            };
        },
        methods:{
            startThinking(){
                this.answer = '';
                this.hasAnswer = false;
                this.isThinking = true;
                setTimeout(() => {
                    this.isThinking = false;
                    this.hasAnswer = true;
                    this.answer = this.possibleAnswers[Math.floor(Math.random()*this.possibleAnswers.length)];
                }, 2000);
            },
        },
    };
</script>

<template>
    <div id="main-div">
        <img src="https://media.istockphoto.com/id/1305166079/vector/billiards-sports-glyph-icon.jpg?s=612x612&w=0&k=20&c=v8ZTv8_6RlAKnkGB0Am3mLvb8T6ubRCN8Wmy8jZ67GU=" alt="8-ball">
        <h1 v-if="isThinking">Thinking ... </h1>

        <h1 v-if="hasAnswer">{{ answer }}</h1>
        <button @click="startThinking">Ask Me a Question!</button>
    </div>
</template>

<style lang="scss" scoped>
    button {
        width: 80%;
        align-self: center;
        margin-top: 8px;
        border-radius: 10%;
        
    };

    img {
        width: 400px;
        border: 1px solid #000000;
        box-sizing: border-box;
        margin-top: 20px;
        margin-bottom: 8px;
    };

    #main-div {
        width: 80%;
        background-color: cornsilk;
        display: flex;
        justify-content: space-between;
        align-items: center;
        flex-direction: column;
        align-items: center;
    }
</style>