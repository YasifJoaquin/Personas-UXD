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
            this.$emit('dato',this.content)
        }
    }
}
</script>

<template>
    <div>
        <slot></slot>
        <br>
        <label class="block font-medium px-9">{{ label }}</label>
        <input type="text" v-model="content" @input="enviarPadre" class="form-input mt-1 block w-full">

    </div>
</template>