<!-- Please remove this file from your project -->
<template>
  <div class="products">
    <h2>Каталог</h2>
    <section class="by_category">
      <h3>Популярные фрукты</h3>
      <div class="products-wrapper">
        <div v-for="(item, key) in products.filter(item => item.acf.category === 'Фрукты')" :key="key" class="item">
          <div class="image">
          <img :src="item.better_featured_image.source_url">
          </div>
          <div class="desc"><h3>{{ item.title.rendered }}</h3>
          <div class="country">Страна: <b>{{ item.acf.countrycountry }}</b></div>
          <div class="min">Минимальный заказ <b>{{ item.acf.min }}{{ item.acf.count_name }}</b></div>
          <div class="price"><span>~</span> <b>{{ item.acf.price }} руб.</b></div>
          <button class="add-to-cart" :class="{green: green}" @click='$emit("addToCart", item)'>в корзину</button>
          </div>
        </div>
      </div>
    </section>
     <section class="by_category">
      <h3>Популярные овощи</h3>
      <div class="products-wrapper">
        <div v-for="(item, key) in products.filter(item => item.acf.category === 'Овощи')" :key="key" class="item">
          <div class="image">
          <img :src="item.better_featured_image.source_url">
          </div>
          <div class="desc"><h3>{{ item.title.rendered }}</h3>
          <div class="country">Страна: <b>{{ item.acf.countrycountry }}</b></div>
          <div class="min">Минимальный заказ <b>{{ item.acf.min }}{{ item.acf.count_name }}</b></div>
          <div class="price"><span>~</span> <b>{{ item.acf.price }} руб.</b></div>
          <button class="add-to-cart" :class="{green: green}" @click='$emit("addToCart", item)'>в корзину</button>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: 'ProductsComponent',
  props: {
    products: {
      type: Array
    },
    green: {
      type: Boolean
    }
  },
  data() {
    return {
      result: this.products,
      categories: [
        'Фрукты', 'Овощи'
      ]
    }
  }
  }
</script>

<style scoped>
.products-wrapper{
	display: flex;
	overflow: auto;
}

.by_category{
  padding: 20px 0;
}
.by_category h3{
  margin-bottom: 16px;
}

.products{
  padding: 16px 0 0 16px;
}
h2{
  text-align: center;
}
.categories{
  display: flex;
  margin-top: 24px;
  margin-bottom: 24px;
  overflow-x: auto;
}
.categories li{
  background: #e5e5e5;
  padding: 5px 10px;
  border-radius: 10px;
  margin-right: 16px;
}
.products-wrapper::-webkit-scrollbar {
	display: none;
  }
.item{
	width: 240px;
	background: #EAEAEA;
	border-radius: 10px;
	overflow: hidden;
	flex: 0 0 auto;
	margin-right: 12px;
}
.image{
	width: 240px;
	height: 200px;
}
.image img{
	max-width: 100%;
	height: 100%;
	object-fit: cover;
}
.desc{
	padding: 16px 8px;
}
.desc h3{
	font-size: 15px;
	font-weight: 700;
	margin-bottom: 8px;
}
.country, .min, .price{
	font-size: 14px;
	margin-bottom: 4px;
}
.price{
	font-size: 16px;
}
.price span{
	color: #1AC034
}
.add-to-cart{
  background: #FF7C00;
  color: #fff;
  border: none;
  width: 100%;
  padding: 10px;
  font-family: inherit;
  text-transform: uppercase;
  border-radius: 10px;
  font-weight: bold;
  transition: all .3s ease;
  cursor: pointer
}
.add-to-cart:focus{
  background: rgb(81, 131, 81);
}
@media (min-width : 1024px) {
  .products{
    width: 900px;
    margin: 0 auto;
  }
	.products-wrapper{
		flex-wrap: wrap;

	}
}
@media (min-width : 1024px) {
  .products{
    width: 1140px;
  }
}
</style>
