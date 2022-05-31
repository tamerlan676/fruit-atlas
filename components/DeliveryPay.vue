<template>
<section class="delivery"><h2>Почему мы?</h2>
	<div class="delivery-wrapper">
	<ul>
		<li> <img class="arrow" width="11px" height="20px" src="~/assets/arrow.svg" alt=""> <div>Мы - команда имеющая 10-летний опыт во фруктово-овощном бизнесне. Мы занимаемся импортом продуктов с Европы, Африки, Азии и Америки.</div></li>
		<li> <img class="arrow" width="11px" height="20px" src="~/assets/arrow.svg" alt=""> <div>Каждый заказа мы собираем как для себя, поэтому готовы вернуть деньги, если качество вас не устроит.</div></li>
		<li> <img class="arrow" width="11px" height="20px" src="~/assets/arrow.svg" alt=""> <div>Стараемся выстроить с клиентами не только рыночные, но и дружеские отношения для дальнейшего сотрудничества.</div></li></ul>
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
	ul li div{
		width: 600px;
	}
}
@media (min-width : 1200px) {
	.delivery-wrapper{
		display: flex;
		align-items: center;
		width: 1140px;
		margin: 0 auto;
	}
	ul{
		margin: 0 auto;
	}
	.girl{
		width: 500px;
	}
}

</style>
