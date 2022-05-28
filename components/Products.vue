<!-- Please remove this file from your project -->
<template>
  <div class="products">
    <h3>Каталог</h3>
    <ul class="categories">
      <li v-for="(cat, key) in categories" :key="key" @click="sortBy(cat)">{{ cat }}</li>
    </ul>
    <div class="products-wrapper">
      <div v-for="(item, key) in result" :key="key" class="item">
        <div class="image">
        <img :src="item.better_featured_image.source_url">
        </div>
        <div class="desc"><h3>{{ item.title.rendered }}</h3>
        <div class="country">Страна: <b>{{ item.acf.countrycountry }}</b></div>
        <div class="min">Минимальный заказ <b>{{ item.acf.min }}{{ item.acf.count_name }}</b></div>
        <div class="price"><span>~</span> <b>{{ item.acf.price }} руб.</b></div>
        <button class="add-to-cart" @click='$emit("addToCart", item)'>в корзину</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ProductsComponent',
  props: {
    products: {
      type: Array
    }
  },
  data() {
    return {
      result: this.products,
      categories: [
        'Фрукты', 'Овощи'
      ]
    }
  },
  methods: {
    sortBy(val = 'Фрукты'){
      if(val === 'Фрукты') { this.result = this.products.filter(item => item.acf.category === 'Фрукты') }
      if(val === 'Овощи') { this.result = this.products.filter(item => item.acf.category === 'Овощи') }
      }
    }
  }
</script>

<style scoped>
.products-wrapper{
	display: flex;
	overflow: auto;
}

.products{
  padding: 16px 0 0 16px;
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
}
.add-to-cart:hover{
  background: #f39944;
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
</style>
