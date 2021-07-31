<template>
    <div>
        <label for="">{{ label }}</label>
        <input 
            type="range"
            v-bind="$attrs"
            :value="value"
            @input="$emit('input', $event.target.value)">
    </div>
</template>

<script>
export default {
    inheritAttrs: false,
    props: {
        label: String,
        value: [Number, String]
    },

    created() {
        console.log('Attrs:', this.$attrs)
    }
}
</script>

<style>

</style>