<template>
  <div class="checkout">
    <div>
      <template>
        <div style="background-color:grey">
          <section class="wrapper">
            <p>Pedido completado</p>
            <router-link
                    :to="{ name: 'Home' }"
                    style="text-decoration:none; width: 5%"
                  >
            <b-button style="width: 450px; background-color: #FFE042; color: black;">
              <b>Ecommerce</b>
            </b-button>
            </router-link>
          </section>
        </div>
      </template>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'

import api_url from "../utils/api";

export default {
  name: "Home",

  components: {},
  created() {
    fetch(api_url("/products"))
      .then((result) => result.json())
      .then((data) => (this.products = data));
  },
  data() {
    return {
      products: [],
    };
  },
  methods: {
    addtoCart(productId, productName, productPrice) {
      fetch(api_url("/cart/"), {
        method: "POST",
        body: JSON.stringify({
          productId: productId,
          productName: productName,
          quantity: 1,
          productPrice: productPrice,
        }),
        headers: {
          "Content-Type": "application/json",
          // 'Content-Type': 'application/x-www-form-urlencoded',
        },
      });
    },
  },
};
</script>
