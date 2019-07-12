<template>
  <div id="app">
    <Header />
    <div class="scrol">
    <div class="container-fluid content">
      <div class="row">
        <ProductTypes @addIngrid="addPizza" v-bind:types="types" />
        <div class="carta">

<p><h2>  можно выбрать 2 продукта из категории</h2>        </p>
        <Cart @delIngrid="delPizza" :cartProducts="selectedProduct" :totalPrice="price" />

              </div>
      </div>
    </div>
    </div>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import ProductTypes from "./components/ProductTypes.vue";
import Cart from "./components/Cart.vue";

export default {
  name: "app",
  components: {
    Header,
    ProductTypes,
    Cart
  },
  data() {
    return {
      types: [
        {
          catId: 0,
          title: "Сыр",
          ingridients: [
            {
              prodId: 3,
              category: 1,
              name: "Пармезан",
              price: 60,
              porc: 1,
              weight: 30,
                 image:'https://ichef.bbci.co.uk/news/976/cpsprodpb/ABBB/production/_105436934_c6128ed2-1e89-4653-abde-f1092a82e2be.jpg',
              img: require('./assets/ingrid/cheese.png')
            },
            {
              prodId: 4,
              category: 1,
              name: "Моцарелла",
              price: 30,
              porc: 1,
              weight: 20,
                 image:'https://ichef.bbci.co.uk/news/976/cpsprodpb/ABBB/production/_105436934_c6128ed2-1e89-4653-abde-f1092a82e2be.jpg',
              img: require('./assets/ingrid/cheese.png')
            }
          ]
        },
        {
          catId: 1,
          title: "Мясо",
          ingridients: [
            {
              prodId: 1,
              category: 0,
              name: "мясо(Курица)",
              price: 100,
              porc: 1,
              weight: 20,
                 image:'http://www.calorizator.ru/sites/default/files/imagecache/recipes_full/recipe/8368.jpg'
            },
            {
              prodId: 2,
              category: 0,
              name: "Салями",
              price: 120,
              porc: 1,
              weight: 20,
            image:'https://upload.wikimedia.org/wikipedia/commons/1/18/Salami_aka.jpg',
              img: require('./assets/ingrid/salyami.png')
            },
            {
              prodId: 2,
              category: 0,
              name: "Охотничьи Колбаски",
              price: 120,
              porc: 1,
              weight: 20,
            image:'https://menunedeli.ru/wp-content/uploads/2018/01/Kolbaski-ohotnichi-kolbaski-s-kartofelem-500x333.jpg',
              img: require('./assets/hunting-sausages.png')
            }
          ]
        },
        {
          catId: 2,
          title: "Овощи",
          ingridients: [
            {
              prodId: 5,
              category: 2,
              name: "Помидор",
              price: 10,
              porc: 1,
              weight: 20,
              image:'https://edaplus.info/food_pictures/big/tomato-types.jpg',
              img: require('./assets/ingrid/pomido.png')
            },
            {
              prodId: 6,
              category: 2,
              name: "Перец",
              price: 9,
              porc: 1,
              weight: 20,
              image:'https://freshmart.com.ua/images/43/mainimg/c52b760fa62440311b3775ebd5991253_big.jpeg',
              img: require('./assets/ingrid/perez.png')
            },
            {
              prodId: 6,
              category: 2,
              name: "Ананас",
              price: 35,
              porc: 1,
              weight: 20,
              image:'https://edaplus.info/food_pictures/pineapple.jpg',
              img:  require('./assets/pineapple.png'),
            }
          ]
        }
      ],
      price: 50,
      selectedProduct: [

        //{ prodId: 0, name: "Основа пиццы", price: 85, weight: 100, porc: 1 }
      ]
    };
  },
  methods: {
    addPizza(elem) {
      let addbool = true;

      if (this.selectedProduct.length == 0) {
        this.selectedProduct.push(elem);
      } else {
        this.selectedProduct.forEach(function(arrayElem) {
          if (arrayElem.prodId == elem.prodId) {
            addbool = false;
          }
        });
        if (addbool == true) {
          this.selectedProduct.push(elem);
        } else {
          addbool = true;
        }
      }
      if (this.selectedProduct.length < 10) {
      addbool = false;
      } else {  addbool = false;}

      this.price = calc(this.selectedProduct);
      console.log(this.price);

      function calc(array){
        let sum=0;
        array.forEach(elem=>{
          sum += elem.price*elem.porc;
        });
        return sum+50;
      }
    },

    delPizza(product) {
      if (product.prodId != 0) {
        let delIndex = 1;
        this.selectedProduct.forEach(function(elem, index) {
          if (elem.prodId == product.prodId) {
            delIndex = index;

          }
        });
        this.selectedProduct.splice(delIndex, 1);

      }
    }
  }
};
</script>

<style>
{
    bottom: 0px;
    height: 0px;
    left: 0px;
    right: 0px;
}
.content{
  margin-top: 20px;

}
#app{
  overflow: scroll;
}

.scrol .scrollar-hscroll {
  overflow: scroll;
  bottom: 0px;
  height: 0px;
  left: 0px;
  right: 0px;
  box-shadow: 0 2px 4px 0 rgba(1,0,0,0.14), 0 3px 4px 0 rgba(0,0,0,0.12), 0 1px 5px 0 rgba(0,0,0,0.20);
}

:active,
:hover,
:focus {
  outline: 0;
  outline-offset: 0;
}

.carta{

     width: 900px;
}
</style>
