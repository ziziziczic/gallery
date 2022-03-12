<template>
<header>
  <div class="menu-container">
    <h1 v-for="menu in menus" :key="menu" class="menu">
        {{menu}}
    </h1>
  </div>
</header>
<section>
  <div class="items-container">
    <div v-for="item in data" :key="item.id">
      <h1>title : {{item.title}}</h1>
      <p>price : {{item.price}}</p>
    </div>
  </div>
</section>


  <!-- <Item v-for="item in data" :key="item.title" :item="item"> -->
    <!-- <Item :item="item"/> -->
  <!-- </Item> -->
</template>

<script>
import data from './assets/data';
// import Item from './components/item';

export default {
  name: 'App',
  data(){
    return {
      menus : ['home','shop','about'],
      data,
    }
  },
  components: {
    // Item,
  },
}
</script>

<style>
  * {padding:0; margin:0;box-sizing: border-box;}
  ul,li{list-style: none;}
  header,section{width:900px;margin:0 auto;}
  .menu-container{display:flex;width:100%;justify-content:space-around;align-items: center;background: darkmagenta;border-radius: 5px;}
  .menu-container h1 {padding:20px;color:#fff;font-weight: 700;}
  .menu-container h1:hover {cursor: pointer; color:yellow;}

  .items-container {width:100%;display:flex;justify-content: space-around;}
  .items-container div {width:100%; flex: 1 1 30%;border:2px solid #eee;margin:5px; display:flex;flex-direction: column;cursor: pointer;}
  .items-container div:first-child {margin-left:0px;}
  .items-container div:nth-child(3n) {margin-right:0px;}
  .items-container div:hover h1{color: red;}
  .items-container h1 {color:darkmagenta;font-weight: 700px; padding:20px; text-align: center;}
  .items-container p {color:#000; padding: 20px;text-align: center;}

</style>
