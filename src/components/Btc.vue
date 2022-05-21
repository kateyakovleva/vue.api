<script>
import { get } from '../util/request'

export default {
  data() {
    return {
      price: 0
    }
  },

  created() {
    this.getCourse();

    let t = this;
    setInterval(() => {
      t.getCourse()
    }, 60000);
  },

  methods: {
    getCourse() {
      let t = this;
      get(
        'https://min-api.cryptocompare.com/data/price?fsym=BTC&tsyms=USD',
        function (response) {
          t.price = response.USD;
        }
      );
    }
  }
}
</script>

<template>
  <div className="div">
    <img className="img marg" src="@/assets/images/bit.png" />
    <div className="text">1 BTC = {{ price }} USD</div>
  </div>
</template>

