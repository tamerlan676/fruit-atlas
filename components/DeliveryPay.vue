<template>
<section class="delivery"><h2>Доставка и оплата</h2>
	<div class="delivery-wrapper">
		<img width="100%" src="~/assets/girl.jpg" alt=""><ul>
		<li> <img class="arrow" width="11px" height="20px" src="~/assets/arrow.svg" alt=""> <div>Цены в каталоге могут отличаться от акутальных цен, так как цена на фрукты и овощи меняется в день по несколько раз</div></li>
		<li> <img class="arrow" width="11px" height="20px" src="~/assets/arrow.svg" alt=""> <div>Оплатить заказ вы можете любым удобным для вас способом. (карта, наличные, перевод)</div></li>
		<li> <img class="arrow" width="11px" height="20px" src="~/assets/arrow.svg" alt=""> <div>Доставка по Москве от заказа на 5000 рублей<br> Привезем в любое удобное для вас время.</div></li></ul>
	</div>
 </section>
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
.delivery{
	padding: 24px 0;
}
.delivery h2{
	text-align: center;
	margin-bottom: 16px;
}
.delivery ul{
	padding: 16px;
	list-style: none;
}
.girl{
	width: 100%;
}
ul li{
	margin-bottom: 16px;
	position: relative;
	display: flex;
	align-items: center;
	justify-content: center;
}
ul li div{
	width: 260px;
}
.arrow{
	margin-right: 16px;
}
@media (min-width : 768px) {
	.girl{
		width: 600px;
		margin: 0 auto;
		display: block;
	}
}
@media (min-width : 1200px) {
	.delivery-wrapper{
		display: flex;
		align-items: center;
	}
	.girl{
		width: 100%;
	}
}

</style>
