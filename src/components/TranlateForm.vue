<template>
  <div class="container">
    <div class="col-6">
      <div class="weather-widget">
        <div class="weather-container">
          <div class="weather-overview">
            <p class="weather-date">{{ result.date }}</p>
            <p class="weather-text">{{ info.city }}</p>
          </div>
          <div class="weather-overview">
            <img
              :src="(result.icon)"
              alt=""
              style="height: 70px"
            />
          </div>
          <div
            class="weather-overview"
            style="display: flex; align-items: center"
          >
            <p class="weather-text">{{ result.degree }}º</p>
            <p class="weather-text" style="font-size: 24px; position: relative">
              {{ result.description }}
            </p>
          </div>
        </div>
        <div class="weather-container">
          <div class="forecast-column">
            <p class="day-header">SUN</p>
            <p class="forecast-icon"><i class="wi wi-day-sleet-storm"></i></p>
            <p class="forecast-temp">17º</p>
            <img
              :src="(result.icon)"
              alt=""
              style="height: 20px"
            />
          </div>
          <!-- <div class="forecast-column">
      <p class="day-header">MON</p>
      <p class="forecast-icon"><i class="wi wi-day-cloudy"></i></p>
      <p class="forecast-temp">22º</p>
      <img  src="https://image.flaticon.com/icons/svg/143/143788.svg" alt="" style="height: 20px;">
    </div>
    <div class="forecast-column">
      <p class="day-header">TUE</p>
      <p class="forecast-icon"><i class="wi wi-day-sunny"></i></p>
      <p class="forecast-temp">25º</p>
      <img  src="https://image.flaticon.com/icons/svg/143/143788.svg" alt="" style="height: 20px;">
    </div>
    <div class="forecast-column">
      <p class="day-header">WED</p>
      <p class="forecast-icon"><i class="wi wi-day-sunny"></i></p>
      <p class="forecast-temp">27º</p>
      <img  src="https://image.flaticon.com/icons/svg/143/143788.svg" alt="" style="height: 20px;">
    </div>
    <div class="forecast-column">
      <p class="day-header">THU</p>
      <p class="forecast-icon"><i class="wi wi-day-showers"></i></p>
      <p class="forecast-temp">20º</p>
      <img  src="https://image.flaticon.com/icons/svg/143/143788.svg" alt="" style="height: 20px;">
    </div>
    <div class="forecast-column">
      <p class="day-header">FRI</p>
      <p class="forecast-icon"><i class="wi wi-cloudy"></i></p>
      <p class="forecast-temp">20º</p>
      <img  src="https://image.flaticon.com/icons/svg/143/143788.svg" alt="" style="height: 20px;">
    </div>
    <div class="forecast-column">
      <p class="day-header">SAT</p>
      <p class="forecast-icon"><i class="wi wi-day-windy"></i></p>
      <p class="forecast-temp">25º</p>
      <img  src="https://image.flaticon.com/icons/svg/143/143788.svg" alt="" style="height: 20px;">
    </div> -->
        </div>
      </div>
    </div>
  </div>
</template>

// https://image.flaticon.com/icons/svg/143/143788.svg

<script>
import axios from "axios";
export default {
  data() {
    return {
      translateText: "",
      translateTo: "",
      info: [],
      result: [],
    };
  },
  methods: {
    translateIt() {
      alert(this.translateTo);
      alert(this.translateText);
    },
  },
  mounted() {
    axios
      .get(
        "https://api.collectapi.com/weather/getWeather?data.lang=tr&data.city=bursa",
        {
          headers: {
            Authorization: `apikey 0SqN7rZI2rmDGyfMrWGuS9:26EubLZxIVmmf1lOEiYWCs`,
            Content: "text/plain; charset=utf-8",
          },
        }
      )
      .then((res) => {
        console.log(res.data);
        this.info = res.data;
      })
      .catch((error) => {
        console.error(error);
      });
  },
  mounted() {
    axios
      .get(
        "https://api.collectapi.com/weather/getWeather?data.lang=tr&data.city=bursa",
        {
          headers: {
            Authorization: `apikey 0SqN7rZI2rmDGyfMrWGuS9:26EubLZxIVmmf1lOEiYWCs`,
            Content: "text/plain; charset=utf-8",
          },
        }
      )
      .then((res) => {
        this.info = res.data;
        this.result = res.data.result[0];
      })
      .catch((error) => {
        console.error(error);
      });
  },
};
</script>
<style scoped>
body {
  font-family: "Titillium Web", sans-serif;
  background: linear-gradient(#007288, #0092aa);
  color: white;

  width: 100vw;
  height: 100vh;
  overflow: hidden;
  margin: 0;
  padding: 10px;
}

.weather-widget {
  width: 600px;
  background-color: rgba(255, 255, 255, 0.15);

  border-style: solid;
  border-radius: 2px;
  border-color: rgba(255, 255, 255, 0.15);
  border-width: 2px;
}

.weather-container {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: flex-start;
}

.weather-overview {
  flex-grow: 1;
  height: 100px;
  width: 200px;

  position: relative;
}

.weather-text {
  font-size: 200%;

  position: absolute;
  top: 30%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.weather-icon {
  font-size: 350%;
  transform: translate(-50%, -90%);
}

.forecast-column {
  width: 85px;
  flex-grow: 1;

  border-style: solid;
  border-color: rgba(255, 255, 255, 0.25);
  border-top-width: 2px;
  border-bottom-width: 0px;
  border-left-width: 0px;
  border-right-width: 2px;
}

.forecast-column:last-of-type {
  border-right-width: 0px;
}

.forecast-column > p {
  text-align: center;
}

.day-header {
  background-color: rgba(255, 255, 255, 0.15);
  padding-top: 5px;
  padding-bottom: 5px;
  font-weight: 600;
  margin: 0;
}

.forecast-icon {
  font-size: 150%;
  margin-bottom: 0px;
}

.forecast-temp {
  font-size: 125%;
}
</style>