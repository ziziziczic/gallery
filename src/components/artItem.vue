<template>
  <div class="item-container">
    <div class="img-container">
        <img :src="item.url" :alt="item.title" class="img">
    </div>
    <h1 @click="$emit('isModal',item.id);">title : {{item.title}}</h1>
    <p>가격 : {{item.price}}</p>
  </div>
</template>

<script>
export default {
    name:'ArtItem',
    props : {
        item : Object,
    }
}
</script>

<style>
  .item-container {flex: 1 0 30%;box-sizing: border-box;border:1px solid #eee; display:flex;flex-direction: column;cursor: pointer;}
  .item-container:first-child {margin-left:0px;}
  .item-container:nth-child(3n) {margin-right:0px;}
  .item-container:hover h1{color: red;}
  .item-container .img-container {width:300px;height:auto; display:flex; justify-content: center; align-items: center;background: #eee;}
  .item-container img{width:100%; height:auto;object-fit: contain;}
  .item-container h1 {color:darkmagenta;font-weight: 700px; padding:20px; text-align: center;}
  .item-container p {color:#000; padding: 20px;text-align: center;}
</style>