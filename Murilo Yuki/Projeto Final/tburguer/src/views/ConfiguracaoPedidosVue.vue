<template>
    <div>
        <h1>Configuração do pedido</h1>
        <pedido-component :burguer="this.hambuguerSelecionado"/> 
    </div>
</template>
<script>
import PedidoComponent from '@/components/PedidoComponent.vue';
    export default {
        name: "ConfiguracaoPedidoVue",
        components: {
            PedidoComponent,
        },
        data(){
            return {
                hambuguerSelecionado: null
            };
        },
        mounted(){
            const query = this.$route.query
            if(query.burguer) {
                const decodeBurguer = JSON.parse(decodeURIComponent(query.burguer));
                this.hamburguerSelecionado = decodeBurguer
            };
        },
    }
</script>
<style scoped> </style>