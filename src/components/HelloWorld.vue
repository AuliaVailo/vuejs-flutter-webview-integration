<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div style="margin: 10px">
      <button @click="bayar" class="button">Bayar</button>
    </div>
    <div style="margin: 10px">
      <button @click="back" class="button">Back To Home</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  created() {
    window.successPayment = this.successPayment;
    window.errorPayment = this.errorPayment;
  },
  methods: {
    bayar: () => {
      console.log("bayar");
      try {
        var payoad = {
          client: "6001",
          _token: "test",
          va_number: "74001002198",
        };
        window.PayVA.postMessage(JSON.stringify(payoad));
      } catch (error) {
        console.log(error);
        alert(error);
      }
    },
    back: () => {
      console.log("Back");
      try {
        window.BackToHome.postMessage("back-to-home");
      } catch (error) {
        console.log(error);
        alert(error);
      }
    },
    successPayment: (value) => {
      console.log(value);
    },
    errorPayment: (value) => {
      console.log(value);
    }
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.button {
  width: 200px;
  margin: 10px;
  height: 50px;
  padding: 10 10 10 10;
}
</style>
