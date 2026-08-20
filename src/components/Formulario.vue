<template>
   <div class="formulario">
        <div class="formulario-titulo">
           {{title}}
        </div>

        <input 
        type="text" 
        class="formulario-input"
        v-model="inputValue">

        <button 
        type="button" 
        :disabled="inputValue.length === 0"
        @click="onSubmit"> 
         {{button}}
        </button>
   </div>
</template>

<script>
export default {
    name: 'Formulario',
    props: {
        title: String,
        button: String,
        action: Function
    },
    data() {
        return {
            inputValue:''
        }
    },
    methods: {
        onSubmit: function () {
            this.action(this.inputValue);
            this.inputValue = '';
        }
    }
}
</script>

<style>
.formulario{
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    justify-content: center;
    margin-top: 20px;
    color: var(--color-title-input);
}

.formulario-input{
    padding: 10px 15px;
    border: 1px solid var(--border-form);
    border-radius: 5px;
    margin: 10px 0;
    background-color: transparent;
    color: white;
    font-size: 1.5rem;
    text-align: center;
}
</style>