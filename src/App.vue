<template>
  <div class="menu-container">
    <div v-for="menu in menus" :key="menu" class="menu">
        {{menu}}
    </div>
  </div>

  <Item v-for="item in data" :key="item.title" :item="item">
    <!-- <Item :item="item"/> -->
  </Item>
</template>

<script>
import data from './assets/data';
import Item from './components/item';

export default {
  name: 'App',
  data(){
    return {
      menus : ['home','shop','about'],
      data,
    }
  },
  components: {
    Item,
  },
}
</script>

<style>
  * {padding:0; margin:0;box-sizing: border-box;}
  ul,li{list-style: none;}
  .menu-container{display:flex; width:900px; justify-content: space-around;align-items: center;background: darkmagenta; margin:0 auto;border-radius: 5px;}
  .menu-container div {padding:10px;color:#fff;font-weight: 700;}
  .menu-container div:hover {cursor: pointer; color:yellow;}

</style>
