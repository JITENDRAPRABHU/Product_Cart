<template>
  <div id="form_template">
    <h1>Create Product</h1>

    <form style="align-content: left; width: 40%">
      <label for="product name">Product Name:</label>

      <input type="text" v-model="productName" required />

      <br />

      <label for="price">Price:</label>

      <input type="number" v-model="price" required />

      <br />
      <input class="button" type="submit" value="Save" />

      <h2>Add to Cart</h2>

      <div id="previewdata">
        <p>Product Name: {{ productName }}</p>

        <p>Price: {{ price }}</p>
        <p>$: {{ total }}</p>
      </div>
    </form>
  </div>
</template>








<script>
export default {
  name: "Test",

  props: {
    msg: String,
  },

  data() {
    return {
      productName: "",

      price: "",
    };
  },

  methods: {
    totalItem: function () {
      let sum = 0;
      this.items.forEach(function (item) {
        sum += parseFloat(item.price) * parseFloat(item.quantity);
      });

      return sum;
    },

    onSubmit() {
      let productReview = {
        productname: this.productname,
        price: this.price,
      };
      this.$emit("review-submitted", productReview);

      this.productname = "";
      this.price = "";
    },
  },
};
</script>




<!-- Add "scoped" attribute to limit CSS to this component only -->

<style scoped>
label {
  display: block;

  margin: 20px 0 10px;

  font-weight: bold;
}

input[type="text"],
input[type="number"],
textarea,
select {
  font-size: 30px;

  border: 1px double rgb(102, 97, 96);

  border-radius: 4px;

  width: 180%;
}

#radioinput input[type="radio"] + label {
  display: inline-block;

  padding: 2px;

  margin: 0 5px;
}

#previewdata {
  color: green;

  font-size: 15px;
}
</style>