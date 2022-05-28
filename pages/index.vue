<template>
  <div>
    <HeaderPanel @turnCart="turnCart" />
    <HeroBlock />
    <WorkScheme />
    <MobileMenu @turnMenu="turnMenu" />
    <Products :products="posts" @addToCart="addToCart" />
    <DeliveryPay />
    <Cart :val="isActive" :products="cart"  @plusOne="plusOne"  
    :totalPrice="this.cart.map(item => item.acf.item_price_count).reduce(function(sum, current) { return sum + current }, 0)" @minusOne="minusOne" @deleteElement="deleteElement" @turnCart="turnCart" />
  </div>
</template>

<script>
import HeaderPanel from '~/components/HeaderPanel.vue';
import HeroBlock from '~/components/HeroBlock.vue';
import MobileMenu from '~/components/MobileMenu.vue';
import Products from '~/components/Products.vue';
import Cart from '~/components/Cart.vue';
import WorkScheme from '~/components/WorkScheme.vue';
import DeliveryPay from '~/components/DeliveryPay.vue';

export default {
    name: 'IndexPage',
    components: { HeaderPanel, HeroBlock, MobileMenu, Products, Cart, WorkScheme, DeliveryPay },
    async asyncData({ $axios }) {
      const posts = await $axios.$get('https://ne404.ru/admin/wp-json/?rest_route=/wp/v2/posts/')
      return { posts }
    },
    data() {
      return{
        isActive: false,
        cart: [],
      }
    },
    head: {
      title: '▷ FruitAtlas - Доставка премиальных овощей и фруктов по Москве',
      description: 'Доставляем фрукты со всего мира к вам на стол',
    },
    methods: {
      turnMenu () {
        this.isActive = !this.isActive
      },
      turnCart () {
        this.isActive = !this.isActive
        if(this.isActive === true){
          document.body.style.overflow = 'hidden'
        }
        else{ document.body.style.overflow = 'visible' }
      },
      addToCart (value) {
        if(this.cart.length){ 
          let isExists = false
          this.cart.map(function(item) { 
            if( item.id === value.id) { 
              isExists = true
              console.log('Уже в корзине')}
            return item })
          if (!isExists) {
            this.cart.push(value)
          }
         }
        else{
          this.cart.push(value)
        }        
        // localStorage.setItem("cart", JSON.stringify(this.cart));
      },
      minusOne (value) {
        if(value.acf.min > 1){
          value.acf.min = value.acf.min - 1
          value.acf.item_price_count = value.acf.item_price_count - value.acf.price
          this.totalPrice = this.cart.map(item => item.acf.price).reduce(function(sum, current) { return sum + current }, 0)
        }  
      },
      plusOne (value) {
        value.acf.min = value.acf.min + 1
        value.acf.item_price_count = value.acf.item_price_count + value.acf.price
        this.totalPrice = this.cart.map(item => item.acf.price).reduce(function(sum, current) { return sum + current }, 0)
      },
      deleteElement (value) {
        this.cart.splice(value, 1)
      }
      }
    }
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:ital,wght@0,400;0,700;1,400;1,700&display=swap');

body {
	font-family: 'Roboto', sans-serif;
	font-size: 16px;
	line-height: 1.65;
	padding: 0;
	margin: 0;
	position: relative;
	overflow-x: hidden;
}

ul, h1, h2, h3 {
  padding: 0;
  margin: 0;
}

ul{
  list-style: none;
}

li a{
  text-decoration: none;
  color: #FF7C00;
}
</style>
