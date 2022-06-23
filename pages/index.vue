<template>
  <div>
    <HeaderPanel @turnCart="turnCart" :count="cart.length" />
    <HeroBlock />
    <MobileMenu />
    <WorkScheme />
    <Products :products="posts" @addToCart="addToCart" />
    <section class="not-found">
      <div class="text">Не нашли то, что искали? Не беда, мы найдем. <br> Просто свяжитесь с нами.</div>
    </section>
    <DeliveryPay />
    <Contacts />
    <Cart :val="isActive" :products="cart" @plusOne="plusOne"
    :totalPrice="this.cart.map(item => item.acf.item_price_count).reduce(function(sum, current) { return sum + current }, 0)" @minusOne="minusOne" @callForm="callForm"  @deleteElement="deleteElement" @turnCart="turnCart" />
    <Form @callForm="callForm" :val="formActive" :cart="cart" />
    <div class="float">
       <a class="call_to_action" target="_blank" href="https://api.whatsapp.com/send/?phone=79188208097&text=Здравствуйте%2C+хочу+заказать+доставку"><img width="60px" height="60px" src="~/assets/whats.svg"></a>
    </div>
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
import Contacts from '~/components/Contacts.vue';
import Form from '~/components/Form.vue';

export default {
    name: 'IndexPage',
    components: { HeaderPanel, HeroBlock, MobileMenu, Products, Cart, WorkScheme, DeliveryPay, Contacts, Form },
    async asyncData({ $axios }) {
      const posts = await $axios.$get('https://fruit-atlas.ru/admin/wp-json/wp/v2/posts?_embed&per_page=100')
      return { posts }
    },
    data() {
      return{
        isActive: false,
        formActive: false,
        cart: []
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
      callForm () {
        this.formActive = !this.formActive
        console.log('form')
      },
      turnCart () {
        this.isActive = !this.isActive
        console.log('turn cart')
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
              isExists = true }
            return item })
          if (!isExists) {
            this.cart.push(value)
          }
         }
        else{
          this.cart.push(value);
        }        
        // localStorage.setItem("cart", JSON.stringify(this.cart));
      },
      minusOne (value) {
        if(value.acf.itemCount > 1){
          value.acf.itemCount = value.acf.itemCount - 1
          value.acf.item_price_count = value.acf.item_price_count - value.acf.price
          this.totalPrice = this.cart.map(item => item.acf.price).reduce(function(sum, current) { return sum - current }, 0)
        }  
      },
      plusOne (value) {
        value.acf.itemCount = value.acf.itemCount + 1
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
.float {
  position: fixed;
  width: 60px;
  height: 60px;
  border: none;
  right: 20px;
  bottom: 50px;
  box-shadow: 0 0 0 0 rgba(40, 150, 36, 0.7);
  border-radius: 50%;
  background-color: #25D366;
  background-size:111%;
  background-position:-5px -5px;
  background-repeat: no-repeat;
  cursor: pointer;
  -webkit-animation: pulse 1.25s infinite cubic-bezier(0.66, 0, 0, 1);
  -moz-animation: pulse 1.25s infinite cubic-bezier(0.66, 0, 0, 1);
  -ms-animation: pulse 1.25s infinite cubic-bezier(0.66, 0, 0, 1);
  animation: pulse 1.25s infinite cubic-bezier(0.66, 0, 0, 1);
}
.not-found{
  padding: 16px;
  text-align: center;
}

.not-found-text{
  width: 100%;
  padding: 10px;
  background: #EAEAEA;
  text-align: center;
}
@media (min-width : 992px) {

}
@-webkit-keyframes pulse {to {box-shadow: 0 0 0 45px rgba(232, 76, 61, 0);}}
@-moz-keyframes pulse {to {box-shadow: 0 0 0 45px rgba(232, 76, 61, 0);}}
@-ms-keyframes pulse {to {box-shadow: 0 0 0 45px rgba(232, 76, 61, 0);}}
      @keyframes pulse {to {box-shadow: 0 0 0 45px rgba(232, 76, 61, 0);}}
</style>
