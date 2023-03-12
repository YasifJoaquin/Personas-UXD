<script>
import axios from "axios";
import inputtxt from '../components/InputsTxt.vue';
import inputnum from '../components/InputsNum.vue';
import inputarea from '../components/InputsTxtArea.vue';
import sliders from "../components/Sliders.vue";
import selects from "../components/Select.vue";


let API_URL = "/api/guardarPersonasUxd.php";

export default {
    components:{
        inputtxt, inputnum, inputarea, sliders, selects
    },
    emits: ['dato','datoedad','dataarea','estadoc','personalidad'],
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
            personalidad1: 50,
            personalidad2: 50,
            personalidad3: 50,
            personalidad4: 50,
            objetivos: " ",
            frustraciones: [],
            motivaciones: [],
            marcas: [],
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
                console.log(this.edad)
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

            situacionsentimental(s){
                this.estadoCivil= s;
                console.log(this.estadoCivil)
            },

            personalidad01(s){
                this.personalidad1 = s
            },
            personalidad02(s){
                this.personalidad2 = s
            },
            personalidad03(s){
                this.personalidad3 = s
            },
            personalidad04(s){
                this.personalidad4 = s
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
                <div>
                    <div class="mb-4">
                        <h1 class="text-3xl font-bold mb-4 text-center">Datos personales</h1>
                        <inputtxt label="Nombre completo" @dato="nombrecompleto"></inputtxt>
                        <inputnum label="Edad" @datoedad="Edad"></inputnum>

                        <div class="mb-4">
                            <selects label="Estado Civil" @estadoc="situacionsentimental" :opciones='{"uno": "Soltero","dos": "Casado","tres": "Divorciado","cuatro": "Separado","cinco": "Union libre","seis": "Viudo"}' />
                        </div>

                        <inputtxt label="Trabajo" @dato="Trabajo"></inputtxt>
                        <inputtxt label="Residencia" @dato="Residencia"></inputtxt>

                        
                    </div>

                    <div class="personalidad">
                        <h1 class="text-3xl font-bold mt-14 text-center mb-8">Personalidad</h1>
                        <sliders @personalidad="personalidad01">Personalidad 1</sliders>
                        <br>
                        <sliders @personalidad="personalidad02">Personalidad 2</sliders>
                        <br>
                        <sliders @personalidad="personalidad03">Personalidad 3</sliders>
                        <br>
                        <sliders @personalidad="personalidad04">Personalidad 4</sliders>
                        <br>
                    </div>

                    <div class="mb-4">
                        <h1 class="text-3xl font-bold mt-4 text-center">Gustos del usuario</h1>
                        <inputarea label="Cita favorita" @dataarea="Cita"></inputarea>
                        <inputtxt label="Autor de la cita" @dato="AutorCita"></inputtxt>
                        <inputarea label="Biografía" @dataarea="Bio"></inputarea>
                        <inputarea label="Marcas" @dataarea="Marcas"></inputarea>
                    </div>
                </div>

                <div class="mt-6">
                    <button @click="Registro()" type="button" class="px-4 py-2 bg-blue-500 text-white rounded hover:bg-blue-600 flex ">Enviar</button>
                </div>
            </form>
        </div>
    </div>
</template>