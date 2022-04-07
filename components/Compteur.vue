<template>
    <div>
        <button @click="decrement">-</button>
        <span>{{value}}</span>
        <button @click="increment">+</button>
    </div>
</template>

<script>
export default {
    data(){
        return {
            value: 0,
        }
    },
    methods: {
        increment (){
            this.value++
        },
        decrement (){
            this.value--
        },
    },
}
</script>