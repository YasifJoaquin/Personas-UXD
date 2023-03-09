<script>
    export default{
        data(){
            return{
                dato:' '
            }
        },
        methods: {
            enviar(){
                this.$emit('dato', this,dialogo)
            }
        }
    }
</script>

<template>
    <div>
        <slot></slot>
        <br>
        <input type="text" class="block text-gray-700 font-bold mb-2" v-model="dato" @input="enviar">
    </div>
</template>