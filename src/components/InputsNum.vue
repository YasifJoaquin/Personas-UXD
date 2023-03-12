<script>
export default {
    props: {
        label: {
            type: String,
            required: true,
            }
    },
    data() {
        return {
            content: ' '
        }
    },
    methods: {
        enviarPadre() {
            this.$emit('datoedad',this.content)
        }
    }
}
</script>

<template>
    <div>
        <slot></slot>
        <br>
        <label class="block font-medium px-9">{{ label }}</label>
        <input type="number" v-model="content" min="10" max="99" class="form-input mt-1 block w-full mb-8" @input="enviarPadre">

    </div>
</template>

