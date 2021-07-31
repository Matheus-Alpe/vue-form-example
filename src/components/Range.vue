<template>
    <div>
        <label for="salario">{{ customLabel }}</label>
        <input 
            id="salario"
            type="range"
            v-bind="$attrs"
            :value="valor"
            :class="inputClasses"
            @change="atualizar">
    </div>
</template>

<script>
export default {
    inheritAttrs: false,
    
    model: {
        // prop: 'value' // 'value' is default
        prop: 'valor',
        // event: 'input' // 'input' is default
        event: 'change'
    },

    props: {
        label: String,
        valor: [Number, String],
        inputClasses: [String, Object, Array]
    },

    computed: {
        customLabel() {
            return `${this.label} R$ ${this.valor || this.$attrs.min}`
        }
    },

    methods: {
        /**
         * @param { InputEvent } event
         */
        atualizar(event) {
            const valor = event.target.value
            this.$emit('change', valor)
            this.valorAtual = valor
        }
    },

    created() {
        console.log('Attrs:', this.$attrs)
    }
}
</script>

<style>

</style>