<template>
<div class="success">
    <img src="~/assets/success.svg" alt="">
    <h1>Ваш заказ принят!</h1>
    <p>Наши сборщики уже бегут работать, а менеджер звонит вам.</p>
    <p>Не убирайте далеко телефон</p>
    <a href="/">Вернуться на сайт</a>
</div>
</template>

<script>
    export default{
        name: 'SuccessPage',
        data() {
            return {
                cart: []
            }
        }
    }
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Roboto:ital,wght@0,400;0,700;1,400;1,700&display=swap');
h1, p, body {
    padding: 0;
    margin: 0;
}

.success{
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    height: 100vh;
	font-family: 'Roboto', sans-serif;
}
h1{
    margin-bottom: 24px;
}
p{
    margin-bottom: 16px;
}
img{
    width: 200px;
}
a{
  color: #FF7C00;
}
</style>