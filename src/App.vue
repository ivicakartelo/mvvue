<template>

  <div
    :style="{
      maxWidth:'700px',
      margin:'auto',
      padding:'20px'
    }"
  >

    <img
      :src="product.image"
      alt=""
      width="100%"
    />

    <h1>
      {{ product.name }}
    </h1>

    <p>
      {{ product.description }}
    </p>

    <h2>
      {{ product.price }} EUR
    </h2>

    <button
      @click="buyBook"
    >
      BUY
    </button>

    <div
      v-if="invoice"
      :style="{
        marginTop:'20px',
        padding:'20px',
        border:'1px solid #ccc'
      }"
    >

      <h2>
        INVOICE
      </h2>

      <p>
        Invoice:
        {{ invoice.number }}
      </p>

      <p>
        Seller:
        {{ invoice.seller }}
      </p>

      <p>
        Product:
        {{ invoice.product }}
      </p>

      <p>
        Total:
        {{ invoice.total }}
        EUR
      </p>

      <p>
        PayPal:
        paypal@example.com
      </p>

    </div>

  </div>

</template>

<script setup>

import { ref } from "vue";

const invoice = ref(null);

const product = {

  name:
    "Modern React Development",

  description:
    "Learn MVP thinking, scalability and architecture.",

  price:
    29,

  image:
    "/images/for_book2.jpg"

};

function buyBook() {

  invoice.value = {

    number:
      "INV-" + Date.now(),

    seller:
      "Modern Web Academy",

    product:
      product.name,

    total:
      product.price

  };

}

</script>