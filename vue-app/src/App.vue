<template>

  <div class='black-bg' v-if='ui_state.IsModalOn == true'>
    <div class='white-bg'>
      <h4>{{ ui_state.current_product_title }}</h4>
      <p>{{ ui_state.current_product_detail }}</p>
      <button @click='btn_onclick_modal_close'>닫기</button>
    </div>
  </div>


  <div class='menu'>
    <a v-for="elem in menus" :key="elem">{{ elem }}</a>
  </div>

  <div class='product' v-for='(elem, i) in products' :key="i">
    <img class='products-img' :src='products[i].image'>
    <h4 class='cls'>{{ products[i].title }}</h4>

    <p :style='price_color'>{{ products[i].price }} 만원</p>
    <button @click='btn_onclick_modal_product_detail(i)'>상세보기</button>
    <button @click='btn_onclick_report(i)'>Report</button> <span>신고수: {{ reports[i] }}</span>
  </div>

  

</template>

<script>
import {products} from './data/posts.js';

export default {
  name: 'App',

  data(){
    return {
      ui_state : {
        IsModalOn : false,
        IsMenuOn : false,
        current_product_title : '',
        current_product_detail : ''
      },
      menus : ['홈', '검색', '마이페이지'],
      products : products,
      reports : [0, 0, 0],
      price_color : 'color: darkgray'
    }
  },

  methods : {
    btn_onclick_report(i){
      this.reports[i] += 1;
    },
    btn_onclick_modal_product_detail(i){
      this.ui_state.current_product_title = this.products[i].title;
      this.ui_state.current_product_detail = this.products[i].content;
      this.ui_state.IsModalOn = true;
    },
    btn_onclick_modal_close(){
      this.ui_state.IsModalOn = false;
    }
  },

  components: {
    
  }
}
</script>

<style>
body {
  margin: 0px;
}

div {
  box-sizing: border-box;
}

.black-bg {
  display: flex;
  justify-content: center;
  width: 100%; height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}

.white-bg {
  display: inline-block;
  width: 50%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}


#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}


.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding: 10px;
}

.product {
  margin-top: 30px;
}

.products-img {
  max-width: 30%;
}

</style>
