<template>
  <header class="container-fluid">

<div id="flag2" class="fr"></div>
    <div class="cell">
      <h1>Pizza</h1>

    </div>
  </header>
</template>

<script>
export default {
  name: 'Header'
}
</script>

<style scoped>
.fr {
  image-rendering: pixelated;
  background-image: url(https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTq-Shh-lOgT6i1P0yqV_77eHrevmu_UdJ40-5dh4Fr2bk7qwO1);
  background-size: 120px 1px;
  background-repeat: repeat;
}

#flag2 {
  min-width: 1520px;
  height: 45px;
}



.cellm{
  background: "black";
  width: 664px;
  background-image: url(http://i.stack.imgur.com/ErVbV.jpg);

}
.container-fluid{
  color: #5124a4;
}

</style>
