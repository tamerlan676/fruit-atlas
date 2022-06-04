<!-- Please remove this file from your project -->
<template>
  <div class="cart" :class="{active: val}">
      <header>
        <h3>Ваш заказ</h3>
        <img @click='$emit("turnCart")' src="~/assets/close.svg">
      </header>
      <div class="empty_cart" v-if="products.length === 0">
        Ваша корзина пока пуста
        <img src="~/assets/empty.svg" alt="">
      </div>
      <section class="list">
        <div v-for="(item, id) in products" :key="id" class="item">
          <img class="foto" :src="item.better_featured_image.source_url">
          <div class="name">
            {{ item.title.rendered }}
            <div class="count">{{ item.acf.min }}{{ item.acf.count_name }}/{{ item.acf.price }}руб</div>
          </div>
          <div class="calc">
            <button @click='$emit("minusOne", item)'>-</button>
            <input v-model="item.acf.itemCount"/>
            <button @click='$emit("plusOne", item)'>+</button>
          </div>
          <div class="price">{{ item.acf.item_price_count }}руб</div>
          <div @click='$emit("deleteElement", id)' class="del">
            <img src="~/assets/del-pr.svg" alt="">
          </div>
        </div>
      </section>
      <footer v-if="products.length > 0">
        <div class="total-price">Итоговая цена: {{ totalPrice }} руб</div>
        <div class="total-price">Минимальный заказ 5000руб</div>
        <button @click='$emit("callForm")'>Оформить заказ</button>
      </footer>
    </div>
</template>
<script>
export default {
  name: 'CartComponent',
  props: {
      val: {
        type: Boolean
      },
      // eslint-disable-next-line vue/require-default-prop
      products: {
        type: Array
      },
      // eslint-disable-next-line vue/require-default-prop
      totalPrice: {
        type: Number
      }
  },
  data() {
    return {
      newCount: 1,
  }},
  methods: {
    callForm() {
      console.log('form')
    }
    }
  }
</script>

<style scoped>
.cart{
  width: 100%;
  background: #fff;
  position: fixed;
  bottom:-100%;
  height: 70vh;
  padding: 8px;
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  transition: all 0.5s ease;
  border-radius: 20px 20px 0 0;
  box-shadow: 1px -1px 4px rgba(0, 0, 0, 0.25);
  z-index: 11;
}
.active{
  bottom: 0;
}
header{
  display: flex;
  justify-content: space-between;
  align-items: center;
}
header img{
  cursor: pointer
}
.list{
  height: 450px;
  overflow-y: scroll;
}
.item{
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 8px;
  border-bottom: 1px solid #e5e5e5;
  padding-bottom: 8px;
}
.name{
  font-weight: 600;
  font-size: 14px;
  width: 100px;
}
.count{
  font-size: 14px;
  font-weight: 400;
}
.item .foto{
  width: 50px;
}
.calc{
  display: flex;
  justify-content: space-between;
}

.calc input{
  width: 25px;
  height: 20px;
  text-align: center;
  border: none
}
.price{
  text-align: right;
  font-size: 14px;
}
.calc button{
  background: orange;
  border: none;
  border-radius: 100%;
  width: 25px;
  height: 25px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: bold;
  font-size: 14px;
  cursor: pointer;
  color: #000
}

.empty_cart{
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}

.del img{
  width: 15px;
}

footer{
  background: #fff;
  padding-top: 30px;
}

footer button{
  width: 100%;
  background: orange;
  border: none;
  height: auto;
  color: #fff;
  font-family: Inherit;
  text-transform: uppercase;
  padding: 15px 10px;
  font-weight: bold;
  font-size: 17px;
  border-radius: 10px;
  cursor: pointer
}
@media (min-width : 992px) {
  .cart{
    width: 60%;
    right: -100%;
    bottom: 0;
    top: 0;
    height: 100%;
    padding: 24px 16px;
    border-radius: 0;
    z-index: 110;
  }
  .active{
    right: 0;
  }
}
@media (min-width : 1200px) {
  .cart{
    width: 30%;
    right: -100%;
  }
  .active{
    right: 0;
  }
}

</style>
