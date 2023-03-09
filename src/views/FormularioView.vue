<script>
import axios from "axios";
let API_URL = "/api/guardarPersonasUxd.php";

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
            personalidad1: " ",
            personalidad2:" ",
            personalidad3: " ",
            personalidad4: " ",
            objetivos: " ",
            frustraciones: [],
            motivaciones: [],
            marcas: " ",
            errors: {}
            }
        },
        mounted() {

        },

        methods: {
            //Funcion para enviar datos a la pagina del maestro
            Registro() {  
                axios
                    .post(API_URL, {

                    //declaracion de variables del backend
                    nombre: this.nombre,
                    edad: this.edad,
                    estadoCivil: this.estadoCivil,
                    trabajo: this.trabajo,
                    residencia: this.residencia,
                    cita: this.cita,
                    citaAutor: this.citaAutor,
                    bio: this.bio,
                    personalidad01: this.personalidad1,
                    personalidad02: this.personalidad2,
                    personalidad03: this.personalidad3,
                    personalidad04: this.personalidad4,
                    objetivos: this.objetivos,
                    frustraciones: this.frustraciones,
                    motivaciones: this.motivaciones,
                    marcas: this.marcas
                    
                    })
                    .then((response) => {
                    //comprobación de envio a la base de datos con numero 200
                    console.log(response.status)
                    });
                
                }
        }
    }
</script>


<template>
    <div class="w-full h-auto bg-amber-300">
        <div class="max-w-md mx-auto bg-amber-500 rounded-xl">
            <h1 class="text-3xl font-semibold mb-4 text-center flex">Formulario de información personal</h1>
            <form method="get" class="px-12">
                <div class="mb-4">
                    <label for="nombre" class="block font-medium px-9">Nombre completo</label>
                    <input id="nombre" v-model="nombre" type="text" class="form-input mt-1 block w-full" :class="{ 'border-red-500': errors.nombre }">
                </div>
                <div class="mb-4">
                    <label for="edad" class="block font-medium px-9">Edad</label>
                    <input id="edad" v-model.number="edad" type="number" min="18" max="99" class="form-input mt-1 block w-full" :class="{ 'border-red-500': errors.edad }">
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
                </div>
                <div class="mb-4">
                    <label for="trabajo" class="block font-medium px-9">Trabajo</label>
                    <input id="trabajo" v-model="trabajo" type="text" class="form-input mt-1 block w-full" :class="{ 'border-red-500': errors.trabajo }">
                </div>
                <div class="mb-4">
                    <label for="residencia" class="block font-medium px-9">Residencia</label>
                    <input id="residencia" v-model="residencia" type="text" class="form-input mt-1 block w-full" :class="{ 'border-red-500': errors.residencia }">
                </div>
                <div class="mb-4">
                    <label for="cita" class="block font-medium px-9">Cita favorita</label>
                    <textarea id="cita" v-model="cita" class="form-textarea mt-1 block w-full h-24" :class="{ 'border-red-500': errors.cita }"></textarea>
                </div>
                <div class="mb-4">
                    <label for="cita-autor" class="block font-medium px-9">Autor de la cita</label>
                    <input id="cita-autor" v-model="citaAutor" type="text" class="form-input mt-1 block w-full" :class="{ 'border-red-500': errors.citaAutor }">
                </div>
                <div class="mb-4">
                    <label for="bio" class="block font-medium px-9">Biografía</label>
                    <textarea id="bio" v-model="bio" class="form-textarea mt-1 block w-full h-32" :class="{ 'border-red-500': errors.bio }"></textarea>
                </div>
                <div class="mt-6">
                    <button @click="Registro()" class="px-4 py-2 bg-blue-500 text-white rounded hover:bg-blue-600 flex ">Enviar</button>
                </div>
            </form>
        </div>
    </div>
</template>