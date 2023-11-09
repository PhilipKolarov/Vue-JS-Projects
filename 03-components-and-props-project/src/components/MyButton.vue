<script>
export default {
    props: {
        btnColor: String,
    },
    emits: ['onClick'],
    data() {
        return {
            count: 0
        }
    },
    methods: {
        onClick() {
            this.count += 1;
            this.btnColor = 'red';
            this.$emit('onClick', this.count);
        }
    }
};
</script>

<template>
    <div>
        <button :style="{ 'background': btnColor }" @click="onClick">I've been clicked {{ count }} times.</button>
    </div>
</template>


<style lang="scss" scoped></style>