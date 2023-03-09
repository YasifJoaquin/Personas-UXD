<script>
    export default {
        data(){
            return {
                contenido: ''
            }
        },
        props: {
            label: {
                type: String,
                required: true,
            },
            value: {
                type: [String, Number],
                required: true,
            },
        },
        methods: {
            enviar() {
                this.$emit('content', this.contenido)
            }
        }
    };
</script>


<template>
    <div>
        <label class="block font-medium px-9">{{ label }}</label>
        <textarea v-model="contentido" @input="enviar" class="form-textarea mt-1 block w-full h-24"></textarea>

    </div>
</template>