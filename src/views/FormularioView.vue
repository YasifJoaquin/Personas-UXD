<script>
import axios from "axios";
import inputtxt from '../components/InputsTxt.vue';
import inputnum from '../components/InputsNum.vue';
import inputarea from '../components/InputsTxtArea.vue';


let API_URL = "/api/guardarPersonasUxd.php";

export default {
    components:{
        inputtxt, inputnum, inputarea
    },
    emits: ['dato','datonum','dataarea'],
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
            nombrecompleto(s){
                this.nombre=s;
            },
            Edad(s){
                this.edad=s;
            },
            Trabajo(s){
                this.trabajo=s;
            },
            Residencia(s){
                this.residencia=s;
            },
            Cita(s){
                this.cita=s;
            },
            AutorCita(s){
                this.citaAutor=s;
            },
            Bio(s){
                this.bio=s;
            },
            Marcas(s){
                this.marcas=s;
            },
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
            <form method="get" class="px-12">
                <div class="grid grid-cols-2 gap-7">
                    <div class="mb-4">
                        <h1 class="text-3xl font-bold mb-4 text-center">Datos personales</h1>
                        <inputtxt label="Nombre completo" v-model="nombrecompleto"></inputtxt>
                        <inputnum label="Edad" v-model="Edad"></inputnum>

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

                        <inputtxt label="Trabajo" v-model="Trabajo"></inputtxt>
                        <inputtxt label="Residencia" v-model="Residencia"></inputtxt>

                        
                    </div>

                    <div class="mb-4">
                        <h1 class="text-3xl font-bold mt-14 text-center">Gustos del usuario</h1>
                        <inputarea label="Cita favorita" @dataarea="Cita"></inputarea>
                        <inputtxt label="Autor de la cita" v-model="AutorCita"></inputtxt>
                        <inputarea label="Biografía" @dataarea="Bio"></inputarea>
                        <inputarea label="Marcas" @dataarea="Marcas"></inputarea>
                    </div>
                </div>

                <div class="mt-6">
                    <button @click="Registro()" class="px-4 py-2 bg-blue-500 text-white rounded hover:bg-blue-600 flex ">Enviar</button>
                </div>
            </form>
        </div>
    </div>
</template>