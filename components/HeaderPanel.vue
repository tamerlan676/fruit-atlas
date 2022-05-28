<!-- Please remove this file from your project -->
<template>
  <header>
    <img src="~assets/logo.svg" alt="Фрут Атлас">
      <ul class="navigation">
        <li><nuxt-link to="#">О компании</nuxt-link></li>
        <li><nuxt-link to="#">О компании</nuxt-link></li>
        <li><nuxt-link to="#">О компании</nuxt-link></li>
        <li><nuxt-link to="#">О компании</nuxt-link></li>
      </ul>
    <div class="burger">
    <span></span>
    </div>
    <div class="cart" @click='$emit("turnCart")'>
      <img src="~assets/cart.svg" alt="">
    </div>
 </header>
</template>

<script>
export default {
  name: 'HeaderPanel',
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
		width: 1140px;
		margin: 0 auto;
	}

}
</style>
