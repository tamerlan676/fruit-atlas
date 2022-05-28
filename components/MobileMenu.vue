<!-- Please remove this file from your project -->
<template>
  <div class="mobile-menu" :class="{active: val}">
    <div class="close-icon" @click='$emit("turnMenu")'>
      <img src="~/assets/close.svg">
    </div>
    <ul>
        <li><nuxt-link to="#">О компании</nuxt-link></li>
        <li><nuxt-link to="#">О компании</nuxt-link></li>
        <li><nuxt-link to="#">О компании</nuxt-link></li>
        <li><nuxt-link to="#">О компании</nuxt-link></li>
        <li><nuxt-link to="#">О компании</nuxt-link></li>
    </ul>
  </div>
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
.mobile-menu{
  position: fixed;
  right: -100%;
  width: 60%;
  padding: 10px 20px;
  z-index: 1;
  top: 0;
  height: 100vh;
  background: #fff;
  transition: all .5s ease ;
}
.mobile-menu li{
  margin-bottom: 16px;
  font-size: 18px;
}
.close-icon{
  display: flex;
  align-items: flex-end;
  justify-content: flex-end;

}
.active{
  right: 0;
}
</style>
