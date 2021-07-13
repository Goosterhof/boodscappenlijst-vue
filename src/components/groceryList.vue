<template>
  <div class="groceryList">
    <h1>Grocery list</h1>
    <table @change="calculateTotal">
        <tr>
          <th>Name</th>
          <th>Price</th>
          <th>Amount</th>
          <th>Total</th>
        </tr>
        <tr v-for="(grocery,index) in groceries" :key="index">
          <td class="name">
            {{grocery.name}}
          </td>
          <td>
            <!-- 
              iets * 100 / 100 = iets 
              is in dit geval dus niet nodig
            -->
            €{{grocery.price.toFixed(2)}}
          </td>
          <td>
            <!-- Je kan v-model.number gebruiken om de waarde om te zetten naar een number -->
            <input id="amount" type="number" min="0" v-model.number="grocery.amount">
            <!-- 
              oninput is oude syntax. Nieuwe syntax gebruik je @input 
              this hoef je nooit aan te geven in de template, die heeft de this context al
              En daarnaast doet deze @input niks
            -->
            <!-- @input="this.value = this.value.replace(/[^0-9.]/g, '').replace(/(\..*)\./g, '$1');" -->
          </td>
          <td>
            <!-- 
              iets * 100 / 100 = iets 
              is in dit geval dus niet nodig
            -->
            €{{grocery.subTotal.toFixed(2)}} 
          </td>
        </tr>
        <tr>
          <td>
            Total
          </td>
          <td>
          </td>
          <td>
          </td>
          <td>
            €{{(Math.round(total * 100) / 100).toFixed(2)}}
          </td>
        </tr>
    </table>
  </div>
</template>

<script>
export default {
  name: 'groceryList',

  data() {
    return {
      groceries: [
        {
          name: "bread",
          price: 1.00,
          amount: 0,
          subTotal: 0
        },
        {
          name: "cheese",
          price: 3.65,
          amount: 0,
          subTotal: 0
        },
        {
          name: "milk",
          price: 1.99,
          amount: 0,
          subTotal: 0
        },
        {
          name: "butter",
          price: 2.45,
          amount: 0,
          subTotal: 0
        }
      ],
      total: 0
    }
  },

  methods: {
    calculateTotal() {
      this.total=0;
      // For of loop is leesbaarder
      // for (let i = 0; i < this.groceries.length; i++) {
      //   this.groceries[i].subTotal = this.groceries[i].amount * this.groceries[i].price;
      //   this.total = this.total + this.groceries[i].subTotal;
      // }

      for (const grocery of this.groceries) {
        grocery.subTotal = grocery.amount * grocery.price
        this.total += grocery.subTotal
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
table, th, td {
  padding: 10px;
  border: 1px solid black;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
}
.name {
  text-transform: capitalize;
}
</style>
