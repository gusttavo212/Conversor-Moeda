<template>
    <div class="conversor">
        <h2>{{moedaA}} Para {{moedaB}}</h2>
        <input type="text" v-model="moedaA_value" v-bind:placeholder="moedaA">
        <input type="button" value="Converter" v-on:click="converter">
        <h2>{{moedaB_value}}</h2>

    </div>
</template>

<script>
export default {//Propriedades do componente que irao ser passadas
    name: "Conversor",
    props: ["moedaA","moedaB"],
    data(){
        return{
            moedaA_value: "",
            moedaB_value: 0
        }
    },
    methods: {
        converter() {
            let de_para = this.moedaA + "_" + this.moedaB        
            let authKey = 'ab633855ed767569f413'
            let url = `https://free.currencyconverterapi.com/api/v6/convert?q=${de_para}&compact=ultra&apiKey=${authKey}`
            
            fetch(url).then(res => {return res.json()})
                            .then(json=>{                                
                                let cotacao = json[de_para]
                                console.log(cotacao)
                                this.moedaB_value = (cotacao * parseFloat(this.moedaA_value)).toFixed(2)
                            })
        }
    }    
}
</script>

<style <style lang="scss" scoped>

</style>


