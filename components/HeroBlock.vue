<template>
  <section class="hero">
    <h1>ОТБОРНЫЕ ФРУКТЫ И ОВОЩИ ВСЕГО МИРА У ВАШЕЙ ДВЕРИ</h1>
    <a href="tel:+79188208097">перезвоните мне</a>
    <a target="_blank" href="https://api.whatsapp.com/send/?phone=79188208097&text=Здравствуйте%2C+хочу+заказать+доставку">заказать в watsapp</a>
 </section>
</template>

<script>
  export default {
    
  }
</script>

<style scoped>
  .hero{
	width: 100%;
	height: 470px;
	background-image: url(../assets/hero.png);
	background-size: cover;
	display: flex;
	flex-direction: column;
	justify-content: center;
	align-items: center;
}
.hero h1{
	text-align: center;
	font-size: 24px;
	width: 266px;
	line-height: 30px;
	margin-bottom: 16px;
	color: #fff
}
.hero a{
	background: #FF7C00;
	display: flex;
	width: 220px;
	align-items: center;
	justify-content: center;
	text-decoration: none;
	color: #fff;
	text-transform: uppercase;
	border-radius: 30px;
	height: 40px;
	margin-bottom: 16px;
	font-weight: 400;
	font-family: inherit;
}
.hero a:last-child{
	border: 2px solid #FF7C00;
	background: transparent;
	margin-bottom: 0;
}
@media (min-width : 992px) {
  .hero{
    align-items: center;
    padding: 0 16px;
  }
}
@media (min-width : 1200px) {
	.hero{
		height: 600px;
	}
	.hero h1{
		font-size: 30px;
		width: 500px;
		line-height: 32px;
	}
}
</style>
