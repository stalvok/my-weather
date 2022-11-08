<template>
  <div v-if="weather !== ''" class="min-h-screen flex flex-col bg-gray"> <!--  вся ширина-->
    <div class="container my-6 px-1 mx-auto h-full">
      <div class="flex flex-col h-full lg:flex-row">
        <div
          class="gap-4 min-w-[336px] bg-white h-full flex flex-col p-2
          items-center rounded-t-[56px] lg:p-6 lg:rounded-l-[56px] lg:rounded-tr-none"
        >
         <div>
           <div class="flex items-center">
             <img class="h-5 mr-3" src="../assets/icons/search-icon.png">
             <input
               type="text"
               class="w-full max-w-[240px] outline-0"
               placeholder="Search for places..."
             >
           </div>
           <img class="h-40 lg:h-56" src="../assets/icons/weather-state1.png">
           <div class="mt-36">
             <div class="text-6xl relative font-light lg:text-7xl lg:self-start">{{kelvinToCelsius}}<span class="text-4xl relative bottom-[20px] lg:bottom-[64px]">°C</span></div>
             <div class="text-xl font-normal lg:text-3xl lg:mt-10 lg:self-start">{{GetCurrentDay()}}</div>
           </div>
         </div>
          <hr class="hr-line">
          <div class="h-1/3 w-full">
            <div class="flex flex-col">
              <div>
                <div class="h-12 capitalize flex items-center text-sm font-semibold gap-4"><img height="32" width="32" src="../assets/icons/cloud-Icon.png">{{weather.list[0].weather[0].description}}</div>
                <div class="h-12 flex items-center text-sm font-semibold gap-4"><img height="32" width="32" src="../assets/icons/rain-small.png">Rain
                  {{weather.list[0].main.humidity}}%</div>
              </div>
              <div class="text-2xl lg:mt-10 lg:h-20 p-4 rounded-xl text-white z-10 bg-center bg-cover text-center relative lg:text-3xl">
                <img class="h-full -m-4 rounded-xl w-full absolute -z-10" src="https://img5.goodfon.ru/original/2048x1284/4/68/nyc-skyline-new-york-in-blue.jpg">
                {{weather.city.country}},{{weather.city.name}}
              </div>
            </div>
          </div>
        </div>
        <div class="flex flex-col p-2 w-full bg-content rounded-b-[56px] lg:rounded-bl-none lg:rounded-r-[56px]">
          <div class="h-64 mt-12 hidden gap-4 lg:flex flex-col lg:flex-row">
            <div class="w-full flex flex-col justify-between bg-white h-[186px] rounded-2xl p-4 items-center">
              <div>{{weekDays[GetCurrentDayShort() + 1]}}</div>
              <img class="h-20" src="../assets/icons/weather-state1.png">
              <div><span>{{weather.list[6].main.temp}} {{weather.list[6].dt_txt}}</span></div>
            </div>
            <div class="w-full flex flex-col justify-between bg-white h-[186px] rounded-2xl p-4 items-center">
              <div>{{weekDays[GetCurrentDayShort() + 2]}}</div>
              <img class="h-20" src="../assets/icons/weather-state1.png">
              <div>{{weather.list[14].main.temp}} {{weather.list[14].dt_txt}}</div>
            </div>
            <div class="w-full flex flex-col justify-between bg-white h-[186px] rounded-2xl p-4 items-center">
              <div>{{weekDays[GetCurrentDayShort() + 3]}}</div>
              <img class="h-20" src="../assets/icons/weather-state1.png">
              <div>{{weather.list[22].main.temp}} {{weather.list[22].dt_txt}}</div>
            </div>
            <div class="w-full flex flex-col justify-between bg-white h-[186px] rounded-2xl p-4 items-center">
              <div>{{weekDays[GetCurrentDayShort() + 4]}}</div>
              <img class="h-20" src="../assets/icons/weather-state1.png">
              <div>{{weather.list[29].main.temp}} {{weather.list[29].dt_txt}}</div>
            </div>
          </div>
          <table class="lg:hidden alight-left text-lg bg-content">
            <tr class="bg-white text-slate-400 text-xl">
              <td>Day</td>
              <td><img class="inline h-5 mr-2" src="../assets/icons/termometr.png">t°</td>
              <td><img class="inline h-5 mr-2" src="../assets/icons/rain-icon.png">Rain</td>
              <td><img class="inline h-5 mr-2" src="../assets/icons/wind-small.png">Wind</td>
            </tr>
            <tr class="bg-white">
              <td>Воскресенье<div class="block">29 октября</div></td>
              <td>9°C</td>
              <td>20</td>
              <td>3 м/с</td>
            </tr>
            <tr class="bg-white">
              <td>Воскресенье<div class="block">29 октября</div></td>
              <td>9°C</td>
              <td>20</td>
              <td>3 м/с</td>
            </tr>
            <tr class="bg-white">
              <td>Воскресенье<div class="block">29 октября</div></td>
              <td>9°C</td>
              <td>20</td>
              <td>3 м/с</td>
            </tr>
            <tr class="bg-white">
                  <td>Воскресенье<div class="block">29 октября</div></td>
                  <td>9°C</td>
                  <td>20</td>
                  <td>3 м/с</td>
                </tr>
          </table>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

import weekday from 'dayjs/plugin/weekday'
import {onMounted} from "vue";
import dayjs from "dayjs"

export default {
  name: "MainPage",
  data () {
    return {
      weather: '',
      weekDays:['Sunday','Monday','Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday'],
      userCity: '',

    }
  },
  methods: {
     async fetchWeather() {
         await fetch('../src/mosk/forecast.json', {
         headers: {
           'Content-Type': 'application/json',
           'Accept': 'application/json'
         }
       })
           .then(res => res.json())
           .then(json => this.weather = json)
      console.log(this.weather,'weather')
    },
    GetCurrentDay() {
       return new Date().toLocaleString("en-US", { weekday: "long" })
    },
    GetCurrentDayShort() {
     return  dayjs().day()

    },

  },
  computed : {
    kelvinToCelsius() {
      return (this.weather.list[0].main.temp - 273.15).toFixed(2).toString()
    }
  },
  mounted() {
    dayjs.extend(weekday)
    this.fetchWeather()
    console.log(new Date().toLocaleString("en-US", { weekday: "long" }),)
    console.log(dayjs().day(),'!!!!!!')
  }
}

</script>

<style scoped>

  div {
  }
  tr td {
    padding: 10px;
  }
  tr:first-child td:first-child { border-top-left-radius: 10px; }
  tr:first-child td:last-child { border-top-right-radius: 10px; }

  tr:last-child td:first-child { border-bottom-left-radius: 10px; }
  tr:last-child td:last-child { border-bottom-right-radius: 10px; }

  tr:first-child td { border-top-style: solid; }
  tr td:first-child { border-left-style: solid; }

</style>