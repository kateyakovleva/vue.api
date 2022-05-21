<script>
import { get } from '../util/request'

export default {
  data() {
    return {
      location: {},
      temp: 0
    }
  },

  created() {
    this.getLocation();
  },

  updated() {
    if (this.location.city) {
      this.getTemp()

      if (this.timer) clearInterval(this.timer)
      this.timer = setInterval(() => {
        this.getTemp()
      }, 60000)
    }
  },

  methods: {
    getLocation() {
      let t = this;
      get(
        'https://ipinfo.io/json?token=e607ddc85bd5c7',
        function (response) {
          t.location = response;
        }
      );
    },

    getTemp() {
      let t = this
      get(
        'https://api.weatherbit.io/v2.0/current?city=' + t.location.city + '&country=' + t.location.country + '&key=1501571fe2ed4fe9b8bf88cf581c0375',
        (response) => {
          t.temp = response.data[0].temp
        }
      )
    }
  }

}

</script>

<template>
  <div className="div">
    <div className="text marg-text">{{ location.city }}, {{ location.country }}</div>
    <div className="text">{{ temp }}°C</div>
  </div>
</template>

