<template>
  <div id="app">
    <div class="container">
      <div class="row">
        <div class="col">
          <h1 class="display-4 text-center">Data Bindings</h1>
          <h4 class="bg-primary text-white p-3">Fruit: {{ fruit }}</h4>
          <h4 class="bg-dark text-white p-3">
            Product: {{ product }} ${{ formattedPrice }}
          </h4>
          <h4 class="bg-secondary text-white p-3">
            Product price with tax: {{ product }} ${{
              getProductPriceWithTax(2)
            }}
          </h4>
          <h4 class="bg-secondary text-white p-3">
            Product price with tax: {{ product }} ${{
              getProductPriceWithTax(5)
            }}
          </h4>
          <h4 class="bg-info text-white p-3">
            Product: {{ product }} {{ productPrice | currencyFilter }}
          </h4>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      fruit: "apples",
      product: "pen",
      productPrice: 4
    };
  },
  computed: {
    formattedPrice() {
      return (this.productPrice + 1).toFixed(2);
    }
  },
  methods: {
    getProductPriceWithTax(tax) {
      this.productPrice = 10;
      let taxValue = this.productPrice * (tax / 100);
      return (this.productPrice + taxValue).toFixed(2);
    }
  },
  filters: {
    currencyFilter(value) {
      return new Intl.NumberFormat("de-DE", {
        style: "currency",
        currency: "EUR"
      }).format(value);
    }
  }
};
</script>
