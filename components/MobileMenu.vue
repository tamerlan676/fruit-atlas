<!-- Please remove this file from your project -->
<template>
  <div class="mobile-menu" :class="{active: val}">
    <ul class="navigation">
        <nuxt-link :to="{ path: '/',hash:'#fruits'}"> <img src="~/assets/fruits.svg" alt=""> Фрукты</nuxt-link>
        <nuxt-link :to="{ path: '/',hash:'#veg'}"><img src="~/assets/vegetables.svg" alt="">Овощи</nuxt-link>
        <nuxt-link :to="{ path: '/',hash:'#citrus'}"><img src="~/assets/citruss.svg" alt="">Цитрусы</nuxt-link>
        <nuxt-link :to="{ path: '/',hash:'#berries'}"> <img src="~/assets/berries.svg">Ягоды</nuxt-link>
        <nuxt-link :to="{ path: '/',hash:'#grass'}"><img src="~/assets/grass.svg">Зелень</nuxt-link>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HeaderPanel',
  props: {
    val: {
      type: Boolean
    }
},
}
</script>

<style scoped>
.mobile-menu{
  position: sticky;
  top: 63px;
  padding-top: 16px;
  background: #fff;
}
.navigation{
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  width: 100%;
}
.navigation a{
  flex: 0 1 auto;
  background: #e5e5e5;
  color: #FF7C00;
  display: flex;
  align-items: center;
  margin-right: 10px;
  margin-bottom: 10px;
  padding: 5px 10px;
  text-decoration: none;
  border-radius: 10px;
}
@media (min-width : 992px) {
  .mobile-menu{
    display: none;
  }
}
</style>
