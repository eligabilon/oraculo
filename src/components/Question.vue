<template>
    <div>
        <h2>Faça uma pergunta cuja resposta seja SIM ou NÃO</h2>
        <form>
            Pergunta: <input type="text" placeholder="Você gosta deste app?" name="pergunta" />
            <input type="submit" value="Enviar" v-on:click="perguntaOraculo">
        </form> 
        <Answer  v-if="oraculoDisse && oraculoDisse.answer" :resposta="oraculoDisse"/>
        <br />
        <input type="submit" value="De novo" v-on:click="reinicia" />
    </div>
    
</template>



<script>
import axios from 'axios'
import Answer from './Answer'

export default {
    name: "Question",
    components: {
        Answer
    },
    data: function() {
        return {
            oraculoDisse: null
        }

    },
    methods: {
        perguntaOraculo: function(e) {
            e.preventDefault()
            axios
                .get('https://yesno.wtf/api')
                .then(response => {
                    console.log(response)
                    this.oraculoDisse = response.data
                })
        }, 
        reinicia: function(e) {
            this.oraculoDisse = nulls
        }
    }
}
</script>



<style>

</style>
