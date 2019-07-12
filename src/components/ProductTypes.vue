<template>
    <div class="col-12 col-md-4">
        <div class="elementContainer text-center" :key="type.id" v-for="type in types">
          <div class="tyr">


            <p class="category-title">{{type.title}}</p>
  </div>
            <div class="ingridients" :key="ing.id" v-for="ing in type.ingridients">

  <img   :src="ing.image" :key="ing.prodId" alt="none" class="img">

                <p class="ingridient-title">{{ing.name}}. {{ing.weight}} грамм/порция </p>
                <span class="dop">Кол-во порций </span>   <input type="text" pattern="\d{1,2}|3" maxlength="1" required v-model="ing.porc"  >
        <span class="dop">Цена(за 1 порцию): {{ing.price}} руб.</span> <br>  <button @click="$emit('addIngrid',ing)">купить</button>

            </div>

        </div>
    </div>
</template>

<script>
export default {
    name: 'ProductTypes',
    data() {
        return {
            message: 1
        }
    },
    props: ['types'],
    // methods: {
    //     addProduct: function (type){
    //         c
    //     }
    // }

}
</script>

<style scoped>
input{
    width: 30px;
    height: 25px;
    border: 2px solid;
    font-size: 20px;
}
a.button{
  display: inline-block;
color: black;
font-size: 125%;
font-weight: 700;
text-decoration: none;
user-select: none;
padding: .25em .5em;
outline: none;
border: 1px solid rgb(250,172,17);
border-radius: 7px;
background: rgb(255,212,3) linear-gradient(rgb(255,212,3), rgb(248,157,23));
box-shadow: inset 0 -2px 1px rgba(0,0,0,0), inset 0 1px 2px rgba(0,0,0,0), inset 0 0 0 60px rgba(255,255,0,0);
transition: box-shadow .2s, border-color .2s;
}
.button:hover {
  box-shadow: inset 0 -1px 1px rgba(0,0,0,0), inset 0 1px 2px rgba(0,0,0,0), inset 0 0 0 60px rgba(255,255,0,.5);
}
.button:active {
  padding: calc(.25em + 1px) .5em calc(.25em - 1px);
  border-color: rgba(177,159,0,1);
  box-shadow: inset 0 -1px 1px rgba(0,0,0,.1), inset 0 1px 2px rgba(0,0,0,.3), inset 0 0 0 60px rgba(255,255,0,.45);
}
.elementContainer{
    color: #000000;
    width: 350px;
    background-color:#FFFFFF;
    padding: 0px 0px 15px 0px;
    margin-bottom: 15px;

    cursor: default;
}
.tyr{
  color: #6262ff;
}
.ingridients{
    border: 1px solid black;
    margin-bottom: 10px;
    padding: 10px 0px;

    background-color:#635258;
}

.elementContainer:hover{
    transition-delay: 1s;
    border: none;
}

.category-title{
    font-size: 18px;
color: #635258;

}

.ingridient-title{
    font-size: 20px;
}
.dop{
    font-family: 'Helvetica',sans-serif;
    color: #e1e1e1;

    font-size: 15px;
    margin-bottom: 5px;
}
.dop p{
    padding: 0;
}
.img{
    height: 45px !important;
    width: 25% !important  ;
}

</style>
