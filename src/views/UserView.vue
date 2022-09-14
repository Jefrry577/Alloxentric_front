<template>
    <div class>
        <v-container>
            <h1>hola</h1>
            <v-form @submit.prevent="post()"
>
                <v-text-field
                v-model= "nombre"
                :counter="30"
                label="Nombre del Model1"
                >
                </v-text-field>
                <v-text-field
                v-model= "atributos.number"
                :counter="30"
                label="Numero del Model1"
                >
                </v-text-field>
                <v-btn
                color="success"
                class="mr-4"
                type="submit"

                >
                Enviar Registro
                </v-btn>
                <v-btn
                color="error"
                class="mr-4"
                >
                Limpiar
                </v-btn>
            </v-form>
        </v-container>
    </div>
</template>
<script lang="ts">
    export default{
        data(){
            return{
                Atributos:[],
                atributos:{
                    name:"",
                    number: ""
                },
                nombre:null
            }
        },
        methods:{
            post(){
                console.log(this.atributos)
                this.axios
                .post("http://localhost:9090/model1", this.atributos)
                .then((res)=>{
                    this.atributos.push(res.data);
                })
                .catch((e)=> {
                    console.log ( e.response ) ;
                })
            }
        }
    }
</script>