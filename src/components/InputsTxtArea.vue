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
            datoarea: ' '
        }
    },
    methods: {
        enviar() {
            this.$emit('dataarea',this.datoarea)
        }
    }
}
</script>

<template>
    <div>
        <slot></slot>
        <br>
        <label class="block font-medium px-9">{{ label }}</label>
        <textarea type="text" v-model="datoarea" class="form-textarea mt-1 block w-full h-24" @input="enviar()"></textarea>

    </div>
</template>