<script>
export default {
    data() {
        return {
            porcentaje: 50
        }
    },
    methods: {
        enviar() {
            this.$emit('personalidad',this.porcentaje)
        }
    }
}
</script>

<template>
    <div>
        <slot></slot>
        <br>
        <input type="range" min="0" max="100" class="bg-gray-200 h-2 w-full rounded-full focus:outline-none focus:ring-blue-500" v-model="porcentaje" @change="enviar">
        <p class="font-semibold text-center">{{ porcentaje }}%</p>
    </div>
</template>