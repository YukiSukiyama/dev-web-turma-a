<template>
    <div>
        <h1>Menu</h1>
        <div id="scroll-horizontal">
            <div id="card-content" v-for="burguer in ListaMenuburguers" 
            :key="burguer.id">
                <div id="card-linha">
                    <div class = "foto-hamburguer">
                        <img 
                        :src="burguer.foto"
                        alt="nome do burger"
                        />
                        <div class="card-coluna">
                            <p id = "nome-content">{{ burguer.nome }}</p>
                            <p id="preco-content">{{burguer.valor}},00</p>
                            <p id = "descricao-content"> {{ burguer.descricao }}</p>
                            <button @click="selecionarBurguer(burguer)">Selecionar</button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
    export default {
        name: "MenuVue",
        data() {
            return{
                ListaMenuburguers: [],
            };
        },
        methods: {
            async consultaMenu(){
                const response = await fetch("http://localhost:3000/menu");
                const dados = await response.json();
                this.ListaMenuburguers = dados.burgues
                console.log(this.ListaMenuburguers)
            },
            selecionarBurguer(burguerSelecionado){
                const param = JSON.stringify(burguerSelecionado);
                const burguerJson = encodeURIComponent(param);
                this.$router.push({path: '/Config',query: {burguer: burguerJson}});
            },
        },
        mounted() {
            this.consultaMenu();
        }
    };
</script>
<style scoped>
    #card-content{
        display: inline-block;
        width: 280px;
        min-height: 500px;
        margin: 20px;
        border: 1px solid white;
        border-radius: 15px;
        box-shadow: 0 4px gray;
        position: relative;
        overflow: hidden;
    }

    #scroll-horizontal{
        flex: 1;
        overflow-x: auto ;
        white-space: nowrap;
        width: 700px;
        margin: 0 auto;
        box-shadow: inset -10px 0px 15px -20px grey;
    }
    .foto-hamburgue img{
        width: 100%;
        object-fit: cover;
        max-height: 200px ;
        border-radius: 10px 0 0;
    }
    #nome-content{
        font-size: 25px;
        font-weight: bold;
        text-align: center;
        width: 100%;
        margin: 12px;
    }
    #preco-content{
        font-size: 35px;
        text-align: center;
        font-weight: bold;
        color: black;
        box-shadow: gray;
        margin: 16px;

    }
    #descricao-content{
        font-size: 16px ;
        text-align: left;
        color: gray;
        margin: 16px;
        white-space: pre-line;
        overflow: hidden;
        text-overflow: ellipsis;
        display: -webkit-box;
        -webkit-line-clamp: 6;
        -webkit-box-orient: vertical;
    }
    .card-coluna button{
        margin-top: auto;
        padding: 10px;
        background-color: rgb(7, 168, 101);
        color: white;
        font-weight: bold;
        border-radius: 8px;
        border: none;
        font-size: 14px;
        width: 100%;
        margin: 20px;
        cursor: pointer;
        transition: 0.5s;
    }
    .card-coluna button:hover{
        background-color: transparent;
        color: darkslategray;
        border-radius: 8px;
        border: solid 1px rgb(53, 108, 121);
    }
</style>