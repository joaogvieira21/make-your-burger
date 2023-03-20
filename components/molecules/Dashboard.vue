<template>
    <h1 class="h1">Gerenciar Pedidos:</h1>
    <div id="burger-table">
      <div>
         <div id="burger-table-heading">
            <div class="order-id">#</div>
            <div>Cliente: </div>
            <div>Pão: </div>
            <div>Carne: </div>
            <div>Opcionais: </div>
            <div>Ações: </div>
         </div>
         <div id="burger-table-rows">
            <div v-for="order in orders" :key="order.id" class="burger-table-row">
               <div class="order-number">{{ order.id }}</div>
               <div>{{ order.name }}</div>
               <div>{{ order.bread }}</div>
               <div>{{ order.meat }}</div>
               <div>
                  <ul>
                     <li v-for="(optional, index) in order.optionals" :key="index">{{ optional }}</li>
                  </ul>
               </div>
               <div>
                  <select name="status" class="status" @change="updateOrder($event, order.id)">
                     <option v-for="s in status" :key="s.id" :value="s.tipo" :selected="order.status == s.tipo"> 
                        {{ s.tipo }}
                     </option>
                  </select>
                  <button class="btn-delete" @click=" deleteOrder(order.id)">
                     Cancelar
                  </button>
               </div>
            </div>
         </div>
      </div>
    </div>
</template>

<script>
   export default {
      data() {
         return {
            orders: null,
            status: null
         }
      },
      methods: {
         async listOrders () {
            const req = await fetch("http://localhost:3000/burgers")
            const data = await req.json()
            this.orders = data

         },
         async deleteOrder (id) {
            const req = await fetch(`http://localhost:3000/burgers/${id}`, {
               method: "DELETE"
            })
            const res = await req.json()
            this.listOrders()
         },
         async updateOrder(e, id) {
            const option = e.target.value
            const dataJson = JSON.stringify( {status:option} )
            const req = await fetch(`http://localhost:3000/burgers/${id}`, {
               method: "PATCH",
               headers: {"Content-Type" : "application/json"},
               body: dataJson
            })

            const res = await req.json()
            console.log(res)
            
         },
         async getStatus () {
            const req = await fetch("http://localhost:3000/status")
            const data = await req.json()
            this.status = data
         }
      },
      mounted() {
         this.listOrders()
         this.getStatus()
      }
   }
</script>


<style>
   .h1 {
      padding: 50px;
   }

   #burger-table {
      max-width: 1200px;
      margin: 0 auto;
      padding-bottom: 300px;

   }


   #burger-table-heading,
   #burger-table-rows,
   .burger-table-row {
      display: flex;
      flex-wrap: wrap;
   }

   #burger-table-heading {
      font-weight: bold;
      padding: 12px;
      border-bottom: 3px solid #333;
   }

   #burger-table-heading div,
   .burger-table-row div {
      width: 19%;
   }

   .burger-table-row {
      width:100%;
      padding:12px;
      border-bottom: 1px solid #CCC;
   }

   #burger-table-heading .order-id,
   .burger-table-row .order-number {
      width: 5%;
   }

   .status {
      padding: 12px 6px;
      margin-right: 12px;
   }

   .btn-delete {
        background-color: black;
        color: gold;
        border: 2px solid white;
        transition: 1.5s;
        height: 50px;
        width: 70px;

    }

    .btn-delete:hover {
        background-color: gold;
        color: black;
        border: 2px solid black;
        font-weight: bolder;
    }
</style>