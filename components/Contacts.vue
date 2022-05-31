<!-- Please remove this file from your project -->
<template>
  <div class="contacts">
    <div class="map">
      <script type="text/javascript" charset="utf-8" async src="https://api-maps.yandex.ru/services/constructor/1.0/js/?um=constructor%3Ab3d762716a0237eecc4c9df9f97f757463a39c5155531dbf89da834b1708f588&amp;width=100%&amp;height=400&amp;lang=ru_RU&amp;scroll=true"></script>
    </div>
    <div class="info">
      <h2>Наши контакты</h2>
      <p>Мы рады ответить на ваши вопросы</p>
      <div class="title">Адрес</div>
      <div class="desc">Мосвка, Калужское ш. 10, Мамыри, Москва 129090</div>
      <div class="title">Телефон</div>
      <div class="desc"> <a href="tel:+79188208097">+79188208097</a> </div>
      <div class="title">Режим работы</div>
      <div class="desc"> Ежедневно с 9:00 до 21:00</div>
    </div>
  </div>
  
</template>

<script>
export default {
  name: 'ContactsComponent',
  data() {
    return {
      newCount: 1,
  }},
  methods: {

    }
  }
</script>

<style scoped>
.contacts{
  width: 100%;
  padding: 24px 0;
}
.map{
  width: 100%;
  height: 400px;
  overflow: hidden;
}
.info{
  padding: 16px;
}

.title{
  font-weight: bold;
}
.desc{
  margin-bottom: 24px;
}


@media (min-width : 1024px) {
  .contacts{
    display: flex;
  }
  .map{
    width: 50%;
    margin-right: 40px;
  }
}

</style>
