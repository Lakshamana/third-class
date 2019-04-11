<template>
    <!--
        Definicao do template HTML da pagina
    -->
    <div>
        <p>{{myData}}</p>
        <span v-bind:title="myData">Examplo de bind </span>
        <div v-if="myConditional">
            <p>My conditional</p>
        </div>
        <div v-show="myConditional">
            <p>My conditional</p>
        </div>        
        <div>
            <button v-on:click="triggerConditional">Trigger condition</button>
        </div>
        <div>
            <input type="text" v-model="myData">
        </div>
        <div>
            <ul v-for="(x,y) in myArray" :key="y">
                <li>{{x}}</li>
            </ul>
        </div>
        <div >
            Computed message : "{{computedString}}"
        </div>
        <div>
            <example-child v-bind:my-string="'Something'"/>
        </div>

        
    </div>
</template>

<script>
/*
Definicao dos scripts, basicamente o javascript do component
*/
import exampleChild from './exampleChild.vue'

export default {
    name:'templateComponent',
    components:{
        //Componentes filhos deste componente.
        exampleChild,
    },
    data:function(){
        //As variaveis do meu compontente ficam aqui
        return {
            myData: 'string',
            myConditional: true,
            myArray:[1,2,3,4]
            }
    },
    methods:{
        //As funcoes do meu componente estao aqui
        myMethod: function(){},
        triggerConditional: function(){
            this.myConditional = !this.myConditional
        }
    },
    computed:{
        //Metodos de tratamento de dados geralmente ficam aqui
        computedString: function(){
            return this.myData.split('').reverse().join('')
        }
    },
    //Funcoes de ciclo de vida dos componentes
    beforeCreate:function(){},
    created:function(){},
    beforeMount:function(){},
    mounted:function(){},
    beforeUpdate:function(){},
    updated: function(){},
    beforeDestroy: function(){},
    destroyed:function(){},

}
</script>

<style>
/*Definicao de estilo exclusivo para o compoment com css ou sass*/
</style>