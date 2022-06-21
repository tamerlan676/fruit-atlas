<!-- Please remove this file from your project -->
<template>
  <header>
    <img src="~assets/logo.svg" alt="Фрут Атлас">
      <ul class="navigation">
        <nuxt-link :to="{ path: '/',hash:'#fruits'}">Фрукты</nuxt-link>
        <nuxt-link :to="{ path: '/',hash:'#veg'}">Овощи</nuxt-link>
        <nuxt-link :to="{ path: '/',hash:'#citrus'}">Цитрусы</nuxt-link>
        <nuxt-link :to="{ path: '/',hash:'#berries'}">Ягоды</nuxt-link>
        <!-- <nuxt-link :to="{ path: '/',hash:'#grass'}">Зелень</nuxt-link> -->
      </ul>
    <div class="burger">
    <span></span>
    </div>
    <div class="cart" @click='$emit("turnCart")'>
      <img src="~assets/cart.svg" alt="">
      <transition name="bounce">
        <div v-if="count" class="count">{{ count }}</div>
      </transition>
    </div>
 </header>
</template>

<script>
export default {
  name: 'HeaderPanel',
  props: {
    count: {
      type: Number
    }
  },
  data () {
    return{
      active: false
    }
  }
}
</script>

<style scoped>
header{
	height: 80px;
	padding: 0 16px;
	display: flex;
	align-items: center;
	justify-content: space-between;
  box-sizing: border-box;
  width: 100%;
  position: sticky;
  top: 0;
  background: #fff;
  z-index: 100;
}
.burger{
	position: relative;
	width: 34px;
	height: 22px;
  display: block;
  display: none;
}
.navigation{
  display: none;
}
.burger:before{
	position: absolute;
	content: '';
	top: 0;
	width: 100%;
	height: 2px;
	background: #FF7C00;
}
.burger span{
	position: absolute;
	content: '';
	right: 0;
	top: 45%;
	width: 80%;
	height: 2px;
	background: #FF7C00;
}
.burger:after{
	position: absolute;
	content: '';
	bottom: 0;
	width: 100%;
	height: 2px;
	background: #FF7C00;
}
.cart{
  position: relative;
  cursor: pointer;
}
.count{
  position: absolute;
  width: 10px;
  height: 10px;
  display: flex;
  align-items: center;
  padding: 5px;
  justify-content: center;
  right: -5px;
  top: 3px;
  background: rgba(243,153,68,.7);
  color: #000;
  border-radius: 100%;
  font-size: 14px;
  font-weight: 600;
}
.bounce-enter-active {
  animation: bounce-in .8s ease-out both;
}

.bounce-leave-active {
  animation: bounce-in .8s reverse ease-in both;
}

@keyframes bounce-in {
  0% {
    transform: scale(0);
  }
  50% {
    transform: scale(1.8);
  }
  100% {
    transform: scale(1);
  }
}
@media (min-width : 992px) {
  .navigation{
    display: flex;
    width: 500px;
    justify-content: space-between;
  }
  .navigation a{
    color: #FF7C00;
    text-decoration: none;
    font-weight: 500;
  }
  .cart{
    display: block;
  }
  .burger{
    display: none;
  }
}

@media (min-width : 1200px) {
	header, .scheme, .products, .delivery{
		width: 100%;
		margin: 0 auto;
	}

}
</style>
