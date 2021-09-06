<template>
  <div class="container">
  <div class="row">
    <div class="col-12 position-absolute top-0 start-50 translate-middle">
      <div class="weather-widget">
        <div class="weather-container">
          <div class="weather-overview">
            <p class="weather-date">{{ day0.date }}</p>
            <p class="weather-text">{{ info.city }}</p>
          </div>
          <div class="weather-overview">
            <img :src="day0.icon" alt="" style="height: 70px" />
          </div>
          <div
            class="weather-overview"
            style="display: flex; align-items: center"
          >
            <p class="weather-text">{{ day0.degree }}º</p>
            <p class="weather-text" style="font-size: 24px; position: relative">
              {{ day0.description }}
            </p>
          </div>
        </div>
        <div class="weather-container">
          <div class="forecast-column">
            <p class="day-header" style="font-size: 12px">{{ day0.date }}</p>
            <p class="forecast-icon"><i class="wi wi-day-sleet-storm"></i></p>
            <p class="forecast-temp">{{ day0.degree }}º</p>
            <img :src="day0.icon" alt="" style="height: 20px" />
            <p class="forecast-temp">{{ day0.description }}</p>

          </div>
          <div class="forecast-column">
            <p class="day-header" style="font-size: 12px">{{ day1.date }}</p>
            <p class="forecast-icon"><i class="wi wi-day-cloudy"></i></p>
            <p class="forecast-temp">{{ day1.degree }}º</p>
            <img :src="day1.icon" alt="" style="height: 20px" />
            <p class="forecast-temp">{{ day1.description }}</p>
          </div>
          <div class="forecast-column">
            <p class="day-header" style="font-size: 12px">{{ day2.date }}</p>
            <p class="forecast-icon"><i class="wi wi-day-sunny"></i></p>
            <p class="forecast-temp">{{ day2.degree }}º</p>
            <img :src="day2.icon" alt="" style="height: 20px" />
            <p class="forecast-temp">{{ day2.description }}</p>
          </div>
          <div class="forecast-column">
            <p class="day-header" style="font-size: 12px">{{ day3.date }}</p>
            <p class="forecast-icon"><i class="wi wi-day-sunny"></i></p>
            <p class="forecast-temp">{{ day3.degree }}º</p>
            <img :src="day3.icon" alt="" style="height: 20px" />
            <p class="forecast-temp">{{ day3.description }}</p>
          </div>
          <div class="forecast-column">
            <p class="day-header" style="font-size: 12px">{{ day4.date }}</p>
            <p class="forecast-icon"><i class="wi wi-day-showers"></i></p>
            <p class="forecast-temp">{{ day4.degree }}º</p>
            <img :src="day4.icon" alt="" style="height: 20px" />
            <p class="forecast-temp">{{ day4.description }}</p>
          </div>
          <div class="forecast-column">
            <p class="day-header" style="font-size: 12px">{{ day5.date }}</p>
            <p class="forecast-icon"><i class="wi wi-cloudy"></i></p>
            <p class="forecast-temp">{{ day5.degree }}º</p>
            <img :src="day5.icon" alt="" style="height: 20px" />
            <p class="forecast-temp">{{ day5.description }}</p>
          </div>
          <div class="forecast-column">
            <p class="day-header" style="font-size: 12px">{{ day6.date }}</p>
            <p class="forecast-icon"><i class="wi wi-day-windy"></i></p>
            <p class="forecast-temp">{{ day6.degree }}º</p>
            <img :src="day6.icon" alt="" style="height: 20px" />
            <p class="forecast-temp">{{ day6.description }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
  </div>
</template>



<script>
import axios from "axios";
export default {
  data() {
    return {
      translateText: "",
      translateTo: "",
      info: [],
      day0: [],
      day1: [],
      day2: [],
      day3: [],
      day4: [],
      day5: [],
      day6: [],
      city:'bursa'
    };
  },
  methods: {
selectedCity(){
  this.city = selectCity
alert(this.city)
},
  },
  mounted() {
    axios
      .get(
        "https://api.collectapi.com/weather/getWeather?data.lang=tr&data.city="+this.city,
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
        this.day0 = res.data.result[0];
        this.day1 = res.data.result[1];
        this.day2 = res.data.result[2];
        this.day3 = res.data.result[3];
        this.day4 = res.data.result[4];
        this.day5 = res.data.result[5];
        this.day6 = res.data.result[6];
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
  justify-content: center;
margin-left: 20%;
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