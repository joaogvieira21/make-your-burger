<template>
    <h1>Monte seu burger:</h1>
    
        <Teste class="form-container" @submit="$event => createBurger($event)" >
            <Msg v-show="msg!==null" :msg="msg"> {{ msg }}</Msg>
            <form id="burger-form" >
                <div class="input-container">
                    <label for="name">Nome do Cliente:</label>
                    <input type="text" id="name" name="name" v-model="name" placeholder="Digite seu nome...">
                </div>
                <div class="input-container">
                    <label for="bread">Escolha o pão:</label>
                    <select name="bread" id="bread" bread="bread" v-model="bread">
                        <option value="">Selecione o item</option>
                        <option v-for="bread in breads" :key="bread.id" :value="bread.tipo"> {{ bread.tipo }}</option>
                    </select>
                </div>
                <div class="input-container">
                    <label for="meat">Escolha a carne do seu burger:</label>
                    <select name="meat" id="meat" meat="meat" v-model="meat">
                        <option value="">Selecione o item</option>
                        <option v-for="meat in meats" :key="meat.id" :value="meat.tipo"> {{ meat.tipo }}</option>
                    </select>
                </div>
                <div class="input-container" >
                    <label for="optional">Selecione os opcionais:</label>
                    <div id="optional-container">
                        <div class="checkbox-container" v-for="optional in optionalData" :key="optional.id">
                            <input type="checkbox" :key="optional.tipo" :value="optional.tipo" name="optionals" v-model="optionals" id="check">
                            <span>{{ optional.tipo }}</span>
                        </div>
                    </div>
                </div>
                <div class="input-container">
                    <input type="submit" value="Enviar Pedido" class="btn-submit">
                </div>
            </form>
        </Teste>
</template>

<script>
    import Msg from '../atoms/Msg.vue'
    export default {
        name: "BurgerForm",
        data() {
            return {
                breads: null,
                meats: null,
                optionalData: null,
                name: null,
                bread: null,
                meat: null,
                optionals: [],
                status: "Solicitado",
                msg: null,
            }
        },
        components: {
            Msg
        },
        methods: {
            async getIngredients () {
                const req = await fetch("http://localhost:3000/ingredientes")
                const data = await req.json()
                
                this.breads = data.paes
                this.meats = data.carnes
                this.optionalData = data.opcionais
                console.log(this.optionalData)
            },
            async createBurger (e) {
                e.preventDefault()
                const data = {
                    name: this.name,
                    bread: this.bread,
                    meat: this.meat,
                    optionals: Array.from(this.optionals),
                    status: "Solicitado"
                }

                const dataJson = JSON.stringify(data);

                const req = await fetch("http://localhost:3000/burgers", {
                    method: "POST",
                    headers: {"Content-Type" : "application/json"},
                    body: dataJson
                })

                const res = await req.json()
                this.name = ""
                this.bread = ""
                this.meat = ""
                this.optionals = []
                this.msg = "Pedido enviado!"
                setTimeout(() => {
                    this.msg = null
                }, 1000)


                
            }
        },
        mounted() {
            this.getIngredients()
            
            
        }
    }
</script>

<style>

    h1 {
        text-align: center;
        font-family: Arial, Helvetica, sans-serif;
        padding: 1px;
    }

    .form-container {
        width: 100%;
        padding: 3em 0;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
    }
    form {
        width: 16%;
    }
    .input-container {
        display: flex;
        flex-direction: column;
        gap: 14px;
        padding: 20px;
    }
    .input-check-container {
        padding: 20px;
        display: flex;
        
    }

    .input-container input, .input-container select {
        width: 250px;
        height: 30px;

    }
    label {
        font-family: Arial, Helvetica, sans-serif;
        border-left: 3px solid goldenrod;
        font-weight: bolder;
        padding-left: 6px;
        display:flex;
        flex-direction: column;
    }
    input::placeholder {
        padding-left:5px
    }
    .checkbox-container {
            display: flex;
            flex-direction: row;
        
            
    }

    #optional-container {
        display:grid;
        grid-template-columns: 50% 50%;
        grid-row-gap: 20px;
        grid-column-gap: 20px;
        width: 200px;
    }
    #check {
        height: 15px;
        width: 20px;
    }
    .btn-submit {
        background-color: black;
        color: gold;
        border: 2px solid white;
        transition: 1.5s;

    }

    .btn-submit:hover {
        background-color: gold;
        color: black;
        border: 2px solid black;
        font-weight: bolder;
    }


  
</style>