<template >
<div class="barscr">


  <div class="col-12 col-md-8">
    <div class="img">
      <img class="ingrid" v-for="product in cartProducts" :src="product.img" :key="product.prodId" >
      <img src="../assets/pizza.png" alt="pizzaimg">
    </div>

    <h3>Цена теста:  50 рублей</h3>

    <table class="table table-no-bordered table-hover">
      <thead class="green">
        <th>Начинка</th>
        <th>Цена</th>
        <th>Вес(порции)</th>
      </thead>
      <tbody>
        <tr :key="product.prodId" v-for="product in cartProducts">

        </tr>
        <tr @click="$emit('delIngrid',product)" :key="product.prodId" v-for="product in cartProducts">
<td>{{product.name}}</td>
          <td>{{product.price * product.porc}} руб.</td>
          <td>{{product.weight*product.porc}} г.</td><td>Удалить заказ</td>
        </tr>
      </tbody>
    </table>
    <div>
      <p>Итоговая цена: {{totalPrice}} руб.</p>
      <button>Сделать заказ</button>
    </div>



  </div>
  </div>
</template>

<script>

export default {
  name: "Cart",
  props: {
    cartProducts: {
      type: Array
    },
    totalPrice: {
      type: Number
    }
  },
};
</script>

<style scoped>



.table{
padding: 900px;

}
.img{
  text-align: center;

}

button{
    border-radius: 10px;
    font-size: 20px;
    background: white;
    border: 2px solid;
    padding: 2px 10px;
    outline: none;
}

.ingrid{
 position: absolute;

}


.md-accent{
 background: rgb(248, 105, 105);
 box-shadow: 0 2px 4px 0 rgba(0,0,0,0.14), 0 3px 4px 0 rgba(0,0,0,0.12), 0 1px 5px 0 rgba(0,0,0,0.20);
}

.small-img{
  height: 100px !important;
  width: 100%;
}
.md-list{
  width: 90%;
    background: 	#FF0000;
  margin-left: 5%;
  box-shadow: 0 2px 4px 0 rgba(1,0,0,0.14), 0 3px 4px 0 rgba(0,0,0,0.12), 0 1px 5px 0 rgba(0,0,0,0.20);
  margin-top: 10px;

}
.md-list-item-text{
  text-align: right;
}
.barscr  .scrollar-vscroll {
  overflow: scroll;
  bottom: 0px;
  height: 0px;
  left: 0px;
  right: 0px;
  box-shadow: 0 2px 4px 0 rgba(1,0,0,0.14), 0 3px 4px 0 rgba(0,0,0,0.12), 0 1px 5px 0 rgba(0,0,0,0.20);
}
</style>
