<template>
   <div class="palavra">
        <div class="palavra-letras">
           <div
                :class="letra === ' ' ? 'palavra-separador' : 'palavra-letra'"
                v-for="(letra, key) in palavra"
                :key="key"
            >
                {{ letra === ' '? '-': (verificarLetra(letra) || etapa === 'enforcado') ? letra : '' }}
            </div>
        </div>

        <div class="palavra-dica">
            {{ dica }}
        </div>
   </div>
</template>

<script>

export default {
    name: 'palavra',
    props: {
        palavra: String,
        dica: String,
        verificarLetra: Function,
        etapa: String
    }
}
</script>

<style>
.palavra{
    color: var(--dica);
    text-transform: uppercase;
    font-size: 1.5rem;
    display: flex;
    flex-direction: column;
    text-align: center;
    align-items: center;
}

.palavra-letras{
    display: flex;
    margin-bottom: 20px;
}

.palavra-letra{
    height: 30px;
    width: 30px;
    margin: 0px 5px;
    border-bottom: 1px solid var(--linha-palavra);
    display: flex;
    justify-content: center;
    align-items: center;
}

.palavra-separador{
    width: 30px;
    display: flex;
    justify-content: center;
    align-items: center;
    border: none;
}
</style>