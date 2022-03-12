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
      <Item v-for="item in data" :key="item.id" :item="item" @isModal="modalopen = true; selectedNum=$event;"/>      
    </div>
  </section>

  <Modal 
    :item="data[selectedNum]" 
    :likeButton ="likeButton"
    :selectedNum = "selectedNum"
    @Minus="$event < 0 ? selectedNum=0 : selectedNum=$event;" 
    @Plus="$event>(data.length-1)? (selectedNum=data.length-1) : selectedNum=$event;"
    @Close="modalopen=false"
    @Like="likeButton[selectedNum] = !likeButton[selectedNum]"
    v-if="modalopen"/>
</template>

<script>
import data from './assets/data';
import Item from './components/artItem.vue';
import Modal from './components/modal.vue';

export default {
  name: 'App',
  data(){
    return {
      menus : ['home','shop','about'],
      data,
      selectedNum : 0,
      modalopen : false,
      likeButton :[false,false,false],
    }
  },
  components: {
    Item,
    Modal,
  },
}
</script>

<style>
  body *{padding:0; margin:0;box-sizing: border-box;}
  ul,li{list-style: none;}
  header,section{width:900px;margin:0 auto;}
  .menu-container{display:flex;width:100%;justify-content:space-around;align-items: center;background: darkmagenta;border-radius: 5px;}
  .menu-container h1 {padding:20px;color:#fff;font-weight: 700;}
  .menu-container h1:hover {cursor: pointer; color:yellow;}

  .items-container {width:100%;display:flex;justify-content: space-around;}
</style>
