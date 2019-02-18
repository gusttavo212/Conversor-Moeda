<template>
    <div class="conversor">
        <h2>{{moedaA}} Para {{moedaB}}</h2>
        <input type="text" v-model="moedaA_value" v-bind:placeholder="moedaA">
        <input class="myButton" type="button" value="Converter" v-on:click="converter">       
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

<style>
    h2, input{
        color: black;
        margin-top: 5px;
    }

    .conversor{
        background-color: #79bbbb;
        width: 40%;
        padding-bottom: 10px;
    }

    .myButton {
	-moz-box-shadow:inset 0px 1px 0px 0px #bbdaf7;
	-webkit-box-shadow:inset 0px 1px 0px 0px #bbdaf7;
	box-shadow:inset 0px 1px 0px 0px #bbdaf7;
	background:-webkit-gradient(linear, left top, left bottom, color-stop(0.05, #79bbff), color-stop(1, #378de5));
	background:-moz-linear-gradient(top, #79bbff 5%, #378de5 100%);
	background:-webkit-linear-gradient(top, #79bbff 5%, #378de5 100%);
	background:-o-linear-gradient(top, #79bbff 5%, #378de5 100%);
	background:-ms-linear-gradient(top, #79bbff 5%, #378de5 100%);
	background:linear-gradient(to bottom, #79bbff 5%, #378de5 100%);
	filter:progid:DXImageTransform.Microsoft.gradient(startColorstr='#79bbff', endColorstr='#378de5',GradientType=0);
	background-color:#79bbff;
	-moz-border-radius:6px;
	-webkit-border-radius:6px;
	border-radius:6px;
	border:1px solid #84bbf3;
	display:inline-block;
	cursor:pointer;
	color:#ffffff;
	font-family:Arial;
	font-size:15px;
	font-weight:bold;
	padding:6px 24px;
	text-decoration:none;
	text-shadow:0px 1px 0px #528ecc;
    margin-left: 5px;
}
.myButton:hover {
	background:-webkit-gradient(linear, left top, left bottom, color-stop(0.05, #378de5), color-stop(1, #79bbff));
	background:-moz-linear-gradient(top, #378de5 5%, #79bbff 100%);
	background:-webkit-linear-gradient(top, #378de5 5%, #79bbff 100%);
	background:-o-linear-gradient(top, #378de5 5%, #79bbff 100%);
	background:-ms-linear-gradient(top, #378de5 5%, #79bbff 100%);
	background:linear-gradient(to bottom, #378de5 5%, #79bbff 100%);
	filter:progid:DXImageTransform.Microsoft.gradient(startColorstr='#378de5', endColorstr='#79bbff',GradientType=0);
	background-color:#378de5;
}
.myButton:active {
	position:relative;
	top:1px;
}

body {
  background: #84fab0;  
}


</style>


