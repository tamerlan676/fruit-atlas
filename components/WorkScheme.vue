<template>
<section class="scheme"><h2>Схема работы</h2>
    <div class="steps-wrapper">
      <div class="step">
      <img src="~/assets/call.svg" alt="">
      <div class="text">Принимаем заказ с сайт, по телефону или по WhatsApp</div>
    </div>
    <div class="step">
      <img src="~/assets/basket.svg" alt="">
      <div class="text">Собираем корзину, отбирая все самое свежее</div>
    </div>
    <div class="step">
      <img src="~/assets/check.svg" alt="">
      <div class="text">Сообщаем вам детали и актуальную цену заказа</div>
    </div>
    <div class="step">
      <img src="~/assets/point.svg" alt="">
      <div class="text">Доставляем ваш заказ прямо до двери вашего дома</div>
    </div>
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
.scheme{
	padding: 50px 16px 0 16px;
}
.scheme h2{
	margin-bottom: 16px;
	text-align: center;
}
.step{
	background: #FF7C00;
	display: flex;
	align-items: center;
	justify-content: center;
	padding: 16px 10px;
	border-radius: 10px;
	line-height: 20px;
	color: #fff;
	margin-bottom: 8px;
}
.step img{
	margin-right: 14px;
	height: 40px;
}
@media (min-width : 768px) {
	.steps-wrapper{
		display: flex;
		flex-wrap: wrap;
		justify-content: center;
		align-items: center;
	}
	.step{
		width: 400px;
		margin-right: 10px;
	}
}
@media (min-width : 1200px) {
	.scheme {
		width: 1120px;
		margin: 0 auto;
	}
}

</style>
