<script>
export default {
    data() {
        return {
            slider: 50,
            value: 0
        }
    },
    props: {
        opciones: Object,
        label: {
            type: String,
            required: true,
            }
    },
    methods: {
        enviar() {
            this.$emit('estadoc',this.value)
        }
    }
    
}
</script>

<template>
    <div>
        <slot ></slot>
        <label class="block font-medium px-9"> {{ label }}</label>
        <select id="estado-civil"  v-model="value" @change="enviar" class="form-select mt-1 block w-full bg-orange-600 text-white">
                            <option value="1">{{ opciones.uno }}</option>
                            <option value="2">{{ opciones.dos }}</option>
                            <option value="3">{{ opciones.tres }}</option>
                            <option value="4">{{ opciones.cuatro }}</option>
                            <option value="5">{{ opciones.cinco }}</option>
                            <option value="6">{{ opciones.seis }}</option>
                            

        </select>
    </div>
</template>