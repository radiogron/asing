<template>
    <div class="asing">
        <img 
            src="../assets/images/asing.png" 
            alt="Asing" 
            class="asing_image"
            @click="bellyClick">
        <transition-group
            name="asing_message"
            tag="div"
            class="asing_messages"
            mode="out-in"
            appear>
            <div 
                class="asing_message"
                v-for="item in messages"
                :key="item.id"
                :style="item.position"
                v-html="item.message">
            </div>
        </transition-group>
    </div>
</template>

<script>
export default {
    name: 'Asing',
    props: {
        messages: Array,
    },
    methods: {
        bellyClick(){
            this.$emit('asingBellyClick');
        }
    }
}
</script>

<style lang="sass" scoped>
.asing
    position: relative
    .asing_image
        max-width: 100%
        cursor: pointer
    .asing_messages
        position: absolute
        left: 0
        top: 0
        height: 100%
        width: 100%
        pointer-events: none
    .asing_message
        position: absolute
        transform: translateX(-50%)
        font:
            size: 2em
            family: 'Caveat', cursive
        text-align: center
        padding: 1rem
        background-color: white
        border: 2px solid black
        &-enter-active, &-leave-active
            transition: all .5s
        &-enter, &-leave-to
            opacity: 0
            transform: translateY(10%) translateX(-50%)
            background-color: transparent
</style>