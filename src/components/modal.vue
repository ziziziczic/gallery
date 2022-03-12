<template>
  <div class="modal">
    <div class="img-container">
        <img :src="item.url" :alt="item.title">
    </div>
    <div class="cont-container">
        <h1>title : {{item.title}}</h1>
        <button :class="likeButton[selectedNum]? `like on`:`like`" @click="$emit('Like')">
            <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-heart" viewBox="0 0 16 16">
            <path d="m8 2.748-.717-.737C5.6.281 2.514.878 1.4 3.053c-.523 1.023-.641 2.5.314 4.385.92 1.815 2.834 3.989 6.286 6.357 3.452-2.368 5.365-4.542 6.286-6.357.955-1.886.838-3.362.314-4.385C13.486.878 10.4.28 8.717 2.01L8 2.748zM8 15C-7.333 4.868 3.279-3.04 7.824 1.143c.06.055.119.112.176.171a3.12 3.12 0 0 1 .176-.17C12.72-3.042 23.333 4.867 8 15z"/>
            </svg>
        </button>
        <div class="profil">
        <p>author : {{item.author}}</p>
        <div>
            <img :src="item.picture" :alt="item.title"/>
        </div>
        </div>
        <p>price : {{item.price}}</p>

        <div class="btn-group">
        <button @click="$emit('Minus',(Number(item.id)-1))">&lt;</button>
        <button @click="$emit('Close')">close</button>
        <button @click="$emit('Plus',(Number(item.id)+1))">&gt;</button>
        </div>
    </div>
  </div>
</template>

<script>
export default {
    name:'Modal',
    props:{
        item: Object,
        likeButton : Array,
        selectedNum : Number,
    }

}
</script>

<style>
  .modal {position:fixed;top:0;left:50%;transform:translateX(-50%);width:900px;height:auto; background:#ddd;padding:10px;border-radius: 5px; display: flex;}
  .img-container{flex-basis: 50%;}
  .img-container img{width:100%;height:auto;}
  .cont-container{position:relative; flex-basis: 50%;padding:10px;display:flex;flex-direction: column;justify-content: space-evenly;align-items: center;}
  .cont-container h1{border-bottom: 1px solid #fff; width:80%; text-align:center;padding-bottom: 5px;}
  .cont-container .like{position:absolute;right:10px;top:10px; background: transparent;border:none;cursor: pointer;}
  .cont-container .like.on{color:red;}
  .cont-container .profil{display: flex; width:100%;justify-content: space-evenly;align-items: center;}
  .cont-container .profil div{width:50%;}
  .cont-container .profil div img{width:150px; height:150px;object-fit: contain;}
  .cont-container .btn-group{width:100%;display: flex; justify-content: space-evenly;}
  .cont-container button {font-size: 1rem;background:#000;color:#fff;outline: none;padding:10px;}
</style>