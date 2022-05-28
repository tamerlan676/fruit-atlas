<template>
<div>
    <h1>Ваш заказ</h1>
    <button>Get Data</button>
    {{ cart }}
</div>
</template>

<script>
    export default{
        name: 'OrderPage',
        data() {
            return {
                cart: []
            }
        },
        created () {
            const arr = localStorage.getItem('cart');
            this.cart = arr
        }
    }
</script>

<style>

</style>