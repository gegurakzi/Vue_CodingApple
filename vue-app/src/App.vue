<template>
  <div class='menu'>
    <a v-for="elem in menus" :key="elem">{{ elem }}</a>
  </div>

  <div v-for='(elem, i) in 3' :key="i">
    <h4 class='cls'>{{ products[i] }} 원룸</h4>
    <p :style='price_color'>{{ prices[i] }} 만원</p>
  </div>

</template>

<script>
export default {
  name: 'App',
  data(){
    return {
      menus : ['홈', '검색', '마이페이지'],
      products : ['역삼', '천호', '마포'],
      prices : [50, 70, 90],
      price_color : 'color: darkgray'
    }
  },
  components: {
  }
}
</script>

<style>
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

</style>
