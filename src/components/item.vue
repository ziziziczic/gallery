<template>
   <div class="img-container">
      <img :src="props.item.url" :alt="props.item.title" class="img">
   </div>
   <p>제목 : {{props.item.title}}</p>
   <p>가격 : {{props.item.price}}</p>
</template>

<script>
export default {
    name:'Item',
    props : {
        item : Object,
    }
}
</script>

<style>
  img{width:100%; height:auto;object-fit: contain;}
  .img-container {width:300px;height:300px; display:flex; align-items: center; border:5px solid #eee;overflow: hidden;}
</style>