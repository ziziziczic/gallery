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
    <div v-for="(item,index) in data" :key="item.id">
      <h1 @click="modalopen=true; selectedNum=index;">title : {{item.title}}</h1>
      <p>price : {{item.price}}</p>
    </div>
  </div>
</section>

<div class="modal" v-if="modalopen">
  <div class="img-container">
    <img :src="data[selectedNum].url" :alt="data[selectedNum].title">
  </div>
  <div class="cont-container">
    <h1>title : {{data[selectedNum].title}}</h1>
    <div class="profil">
      <p>author : {{data[selectedNum].author}}</p>
      <div>
        <img :src="data[selectedNum].picture" :alt="data[selectedNum].title"/>
      </div>
    </div>
    <p>price : {{data[selectedNum].price}}</p>
    <button @click="modalopen=false">close</button>
  </div>
</div>

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
      selectedNum : 0,
      modalopen : false,
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

  .modal {position:fixed;top:0;left:50%;transform:translateX(-50%);width:900px; background:#ddd;padding:10px;border-radius: 5px; display: flex;}
  .img-container{flex-basis: 50%;}
  .img-container img{width:100%;height:auto;}
  .cont-container{flex-basis: 50%;padding:10px;display:flex;flex-direction: column;justify-content: space-evenly;align-items: center;}
  .cont-container .profil{display: flex; width:100%;justify-content: space-evenly;align-items: center;}
  .cont-container .profil div{width:50%;}
  .cont-container .profil div img{width:150px; height:150px;object-fit: contain;}
  .cont-container button {font-size: 1rem;background: #fff;outline: none;padding:10px;}

</style>
