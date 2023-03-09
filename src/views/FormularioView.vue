<template>
    <div class="w-full h-auto bg-amber-300">
        <div class="max-w-md mx-auto bg-amber-500 rounded-xl">
            <h1 class="text-3xl font-semibold mb-4 text-center flex">Formulario de información personal</h1>
            <form @submit.prevent="submitForm" class="px-12">
                <div class="mb-4">
                    <label for="nombre" class="block font-medium px-9">Nombre completo</label>
                    <input id="nombre" v-model="nombre" type="text" class="form-input mt-1 block w-full" :class="{ 'border-red-500': errors.nombre }">
                    <p v-if="errors.nombre" class="text-red-500 text-sm mt-1">{{ errors.nombre }}</p>
                </div>
                <div class="mb-4">
                    <label for="edad" class="block font-medium px-9">Edad</label>
                    <input id="edad" v-model.number="edad" type="number" min="18" max="99" class="form-input mt-1 block w-full" :class="{ 'border-red-500': errors.edad }">
                    <p v-if="errors.edad" class="text-red-500 text-sm mt-1">{{ errors.edad }}</p>
                </div>
                <div class="mb-4">
                    <label for="estado-civil" class="block font-medium px-9">Estado civil</label>
                    <select id="estado-civil" v-model.number="estadoCivil" class="form-select mt-1 block w-full bg-orange-600 text-white" :class="{ 'border-red-500': errors.estadoCivil }">
                        <option value="1">Soltero</option>
                        <option value="2">Casado</option>
                        <option value="3">Divorciado</option>
                        <option value="4">Separado</option>
                        <option value="5">Unión libre</option>
                        <option value="6">Viudo</option>
                    </select>
                    <p v-if="errors.estadoCivil" class="text-red-500 text-sm mt-1">{{ errors.estadoCivil }}</p>
                </div>
                <div class="mb-4">
                    <label for="trabajo" class="block font-medium px-9">Trabajo</label>
                    <input id="trabajo" v-model="trabajo" type="text" class="form-input mt-1 block w-full" :class="{ 'border-red-500': errors.trabajo }">
                    <p v-if="errors.trabajo" class="text-red-500 text-sm mt-1">{{ errors.trabajo }}</p>
                </div>
                <div class="mb-4">
                    <label for="residencia" class="block font-medium px-9">Residencia</label>
                    <input id="residencia" v-model="residencia" type="text" class="form-input mt-1 block w-full" :class="{ 'border-red-500': errors.residencia }">
                    <p v-if="errors.residencia" class="text-red-500 text-sm mt-1">{{ errors.residencia }}</p>
                </div>
                <div class="mb-4">
                    <label for="cita" class="block font-medium px-9">Cita favorita</label>
                    <textarea id="cita" v-model="cita" class="form-textarea mt-1 block w-full h-24" :class="{ 'border-red-500': errors.cita }"></textarea>
                    <p v-if="errors.cita" class="text-red-500 text-sm mt-1">{{ errors.cita }}</p>
                </div>
                <div class="mb-4">
                    <label for="cita-autor" class="block font-medium px-9">Autor de la cita</label>
                    <input id="cita-autor" v-model="citaAutor" type="text" class="form-input mt-1 block w-full" :class="{ 'border-red-500': errors.citaAutor }">
                    <p v-if="errors.citaAutor" class="text-red-500 text-sm mt-1">{{ errors.citaAutor }}</p>
                </div>
                <div class="mb-4">
                    <label for="bio" class="block font-medium px-9">Biografía</label>
                    <textarea id="bio" v-model="bio" class="form-textarea mt-1 block w-full h-32" :class="{ 'border-red-500': errors.bio }"></textarea>
                    <p v-if="errors.bio" class="text-red-500 text-sm mt-1">{{ errors.bio }}</p>
                </div>
                <div class="mt-6">
                    <button type="submit" class="px-4 py-2 bg-blue-500 text-white rounded hover:bg-blue-600 flex ">Enviar</button>
                </div>
            </form>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
        nombre: '',
        edad: '',
        estadoCivil: '',
        trabajo: '',
        residencia: '',
        cita: '',
        citaAutor: '',
        bio: '',
        errors: {}
        }
    },
    methods: {
        submitForm() {
        // Validación de campos
        this.errors = {}
        if (!this.nombre) {
            this.errors.nombre = 'El nombre es obligatorio'
        }
        if (!this.edad) {
            this.errors.edad = 'La edad es obligatoria'
        }
        if (!this.estadoCivil) {
            this.errors.estadoCivil = 'El estado civil es obligatorio'
        }
        if (!this.trabajo) {
            this.errors.trabajo = 'El trabajo es obligatorio'
        }
        if (!this.residencia) {
            this.errors.residencia = 'La residencia es obligatoria'
        }
        if (!this.cita) {
            this.errors.cita = 'La cita favorita es obligatoria'
        }
        if (!this.citaAutor) {
            this.errors.citaAutor = 'El autor de la cita es obligatorio'
        }
        if (!this.bio) {
            this.errors.bio = 'La biografía es obligatoria'
        }

        // Si no hay errores, enviar formulario
        if (Object.keys(this.errors).length === 0) {
            alert('Formulario enviado')
            // Aquí se enviaría el formulario a través de una petición AJAX o similar
        }
        }
    }
    }
</script>