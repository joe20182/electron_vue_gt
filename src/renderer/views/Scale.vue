<template>
    <div class="scale-wrapper">
        <p>{{num}}</p>
        <button @click="add">+</button>
    </div>
</template>

<script>
export default {
    name: 'Scale',
    data() {
        return {
            num: 0
        }
    },
    methods: {
        add() {
            this.num ++;
        }
    }
}
</script>

<style lang="scss">
.scale-wrapper {
    button {
        padding: 10px;
        background-color: #ccc;
        border-radius: 5px;
    }
}
</style>
