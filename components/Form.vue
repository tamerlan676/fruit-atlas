<!-- Please remove this file from your project -->
<template>
  <div class="form" :class="{active: val}">
      <header>
        <h3>Форма отправки</h3>
        <img @click='$emit("callForm")' src="~/assets/back.svg" alt="">
      </header>
      <form @submit.prevent="submit" action="">
      <section>
        <div class="input">
          <label for="Как вас зовут?">Как вас зовут?</label>
          <input required v-model="name" type="text" placeholder="Денис, Мария" >
        </div>
        <div class="input">
          <label for="Как вас зовут?">Ваш Телефон</label>
          <input required v-model="phone" type="text"  placeholder="7(999) 999-99-99">
        </div>
        <div class="input">
          <label for="Как вас зовут?">По какому адресу доставить?</label>
          <textarea required v-model="adress" placeholder="Москва, ул Пушкинаб 17 кв 99"></textarea>
        </div>
      </section>
      <footer>
        <button type="submit">Отправить</button>
      </footer>
      {{ order }}
      </form>
    </div>
</template>
<script>
import axios from 'axios'
export default {
  name: 'FormComponent',
  props: {
      val: {
        type: Boolean
      },
      cart: {
        type: Array
      }
  },
  data () {
    return {
      name: '',
      phone: '',
      adress: '',
      order: '',
    }
  },
  methods: {
    submit() {
        const list = this.cart.map((item, index) =>  (index + 1) + ' ' + item.title.rendered + ' - ' + item.acf.itemCount + ' ' + item.acf.item_price_count )
        const totalPrice = this.cart.map(item => item.acf.item_price_count).reduce(function(sum, current) { return sum + current }, 0)
        const enter = '\n'
        const order = {
          name: this.name,
          phone: this.phone,
          adress: this.adress,
          products: list.join().replace(/,/g, enter )
        }
        const message = `<strong>${order.name}</strong> заказал(а) \n <pre>${order.products}</pre> \n на сумму: ${totalPrice} руб \n Тел: <strong><a href="tel:+${order.phone}">${order.phone}</a></strong> \n Адрес: <i>${order.adress}</i>` 
        axios.post(`https://api.telegram.org/bot5561581589:AAHOqK8z6VzxVouFK0m-pC9u-HruGIPALfs/sendMessage`, {
          chat_id: '-1001187047227',
          parse_mode: 'html',
          text: message
        }).then()
    }
  }
}
</script>

<style scoped>
.form{
  width: 100%;
  background: #fff;
  position: fixed;
  bottom:-100%;
  height: 70vh;
  padding: 8px;
  box-sizing: border-box;
  transition: all 0.5s ease;
  border-radius: 20px 20px 0 0;
  box-shadow: 1px -1px 4px rgba(0, 0, 0, 0.25);
  z-index: 12;
}
.active{
  bottom: 0;
}
header{
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 24px;
}
label{
  font-weight: bold;
  display: block;
  margin-bottom: 8px;
}
input{
  width: 100%;
  border:1px solid rgb(206, 153, 55);
  border-radius: 5px;
  height: 40px;
  box-sizing: border-box;
  padding-left: 12px;
  font-family: inherit;
  font-size: 16px;
}
.input{
  margin-bottom: 24px;
}
.tip{
  font-size: 14px;
  line-height: 18px;
}
textarea{
  width: 100%;
  border:1px solid rgb(206, 153, 55);
  border-radius: 5px;
  height: 90px;
  box-sizing: border-box;
  padding-left: 12px;
  font-family: inherit;
  font-size: 16px;
  padding-top: 12px;
}
header img{
  cursor: pointer
}
.name{
  font-weight: 600;
  font-size: 14px;
  width: 100px;
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
}
@media (min-width : 992px) {
  .form{
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
  .form{
    width: 30%;
    right: -100%;
  }
  .active{
    right: 0;
  }
}

</style>
