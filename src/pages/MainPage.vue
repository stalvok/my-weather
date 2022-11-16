<template>
  <div v-if="weather !== ''" class="min-h-screen flex flex-col bg-gray px-2"> <!--  вся ширина-->
    <div class="container my-16 px-1 max-w-[1280px] mx-auto">
      <div class="flex flex-col lg:flex-row">
        <div class="gap-4 bg-white flex flex-col p-2
          items-center rounded-t-[56px] lg:p-11 lg:rounded-l-[56px] lg:rounded-tr-none"
        >
          <div class="flex items-center gap-2">
            <img class="h-5 " src="../assets/icons/search-icon.png">
            <input
              class="w-full max-w-[240px] pl-4 focus:bg-gray-200 rounded-2xl py-2 px-1 font-semibold"
              placeholder="Search for places..."
            >
        </div>
          <div class="flex lg:flex-col flex-row">
           <img
             class="mt-6 lg:w-[320px]"
             src="../assets/icons/weather-state1.png">
           <div class="mt-12">
             <div class="text-6xl lg:text-9xl">{{kelvinToCelsius(this.weather.list[0].main.temp)}}
               <span class="text-4xl relative bottom-[20px] lg:bottom-[64px]">°C</span>
             </div>
             <div class="text-xl lg:text-3xl lg:mt-10">{{GetCurrentDay()}}</div>
           </div>
          </div>
          <hr class="hr-line">
          <div class="w-full">
            <div class="flex lg:flex-col flex-row justify-around">
              <div>
                <div class="h-12 text-sm lg:text-xl capitalize flex items-center font-semibold gap-4">
                  <img width="32" src="../assets/icons/cloud-Icon.png">{{weather.list[0].weather[0].description}}
                </div>
                <div class="h-12 flex items-center text-sm lg:text-xl font-semibold gap-4">
                  <img width="32" src="../assets/icons/rain-small.png">Rain
                  {{weather.list[0].main.humidity}}%</div>
              </div>
              <div
                  class="text-2xl flex items-center justify-center
                  lg:mt-10 p-8 rounded-xl text-white z-10 bg-center bg-cover relative lg:text-3xl">
                <img
                  class="h-full w-[240px] rounded-xl lg:w-full absolute -z-10"
                  src="../assets/img/new-york-bg.jpg"
                >
                {{weather.city.country}},{{weather.city.name}}
              </div>
            </div>
          </div>
        </div>
        <div class="flex flex-col p-11 w-full bg-content rounded-b-[46px] lg:rounded-bl-none lg:rounded-r-[46px]">
          <div class="lg:flex justify-between font-bold text-slate-400 text-2xl hidden">
            <div>
              <span class="hover:text-black">Today</span>
              <span class="text-black underline pl-6 underline-offset-8">Week</span>
            </div>
            <div class="text-2xl flex items-center gap-4">
              <span class="px-3 py-2 bg-black rounded-full text-white">°C</span>
              <span class="text-black px-3 py-2 bg-white rounded-full">°F</span>
              <img class="w-14 h-14 ml-8 rounded-xl" src="../assets/img/indian-2.jpg">
            </div>
          </div>
          <div class="mt-12 hidden gap-4 lg:grid lg:grid-cols-4 xl:grid-cols-7">
            <div class="weeks-day-card">
              <div class="font-semibold">{{GetCurrentDayShort(1)}}</div>
              <img class="h-16" src="../assets/icons/weather-state1.png">
              <div><span>{{kelvinToCelsius(weather.list[6].main.temp)}}°C</span></div>
            </div>
            <div class="weeks-day-card">
              <div class="font-semibold">{{GetCurrentDayShort(2)}}</div>
              <img class="h-16" src="../assets/icons/weather-state1.png">
              <div>{{kelvinToCelsius(weather.list[14].main.temp)}}°C</div>
            </div>
            <div class="weeks-day-card">
              <div class="font-semibold">{{GetCurrentDayShort(3)}}</div>
              <img class="h-16" src="../assets/icons/weather-state1.png">
              <div>{{kelvinToCelsius(weather.list[22].main.temp)}}°C</div>
            </div>
            <div class="weeks-day-card">
              <div class="font-semibold">{{GetCurrentDayShort(4)}}</div>
              <img class="h-16" src="../assets/icons/weather-state1.png">
              <div>{{kelvinToCelsius(weather.list[29].main.temp)}}°C</div>
            </div>
            <div class="weeks-day-card">
              <div class="font-semibold">{{GetCurrentDayShort(5)}}</div>
              <img class="h-16" src="../assets/icons/weather-state1.png">
              <div>{{kelvinToCelsius(weather.list[36].main.temp)}}°C</div>
            </div>
            <div class="weeks-day-card">
              <div class="font-semibold">{{GetCurrentDayShort(6)}}</div>
              <img class="h-16" src="../assets/icons/weather-state1.png">
              <div>{{kelvinToCelsius(weather.list[36].main.temp)}}°C</div>
            </div>
            <div class="weeks-day-card">
            <div class="font-semibold">{{GetCurrentDayShort(7)}}</div>
            <img class="h-16" src="../assets/icons/weather-state1.png">
            <div>{{kelvinToCelsius(weather.list[36].main.temp)}}°C</div>
          </div>
          </div>
          <div class="hidden lg:flex h-full lg:mt-28 xl:mt-12 flex-col">
            <div class="font-semibold text-4xl">Today's Highlights</div>
            <div class="grid lg:grid-cols-2 xl:grid-cols-3 xl:auto-rows-[224px] content-end h-full gap-4">
              <div class="highlights-card">
                <div class="text-xl text-slate-400">Humidity</div>
                <div class="text-5xl font-semibold">{{weather.list[0].main.humidity}}%</div>
                <div class="text-xl">Normal</div>
              </div>
              <div class="lg:gap-6 xl:gap-0 highlights-card">
                <div class="text-xl text-slate-400">
                  UV index
                </div>
                <div>
                  <div class="relative flex w-[200px] mx-auto justify-center">
                    <div class="progress">
                      <div class="barOverflow">
                        <div class="bar"></div>
                      </div>
                      <span class="text-5xl relative bottom-[40px]">5</span>
                    </div>
                    <div class="absolute text-slate-400 -left-[4%] text-xl bottom-[30%]">0</div>
                    <div class="absolute text-slate-400 left-[6%] text-xl bottom-[78%]">3</div>
                    <div class="absolute text-slate-400 left-[50%] text-xl bottom-[100%]">6</div>
                    <div class="absolute text-slate-400 left-[88%] text-xl bottom-[78%]">9</div>
                    <div class="absolute text-slate-400 left-[98%] text-xl bottom-[30%]">12</div>
                  </div>
                </div>
              </div>
              <div class="highlights-card">
                <div class="text-xl text-slate-400">
                  Wind Status
                </div>
                <div class="text-5xl font-semibold">
                  {{weather.list[0].wind.speed}}
                </div>
                <div class="text-xl">
                  WSW
                </div>
              </div>
              <div class="highlights-card">
                <div class="text-xl text-slate-400">
                  Visibility
                </div>
                <div class="text-5xl font-semibold">
                  {{weather.list[0].visibility}}
                </div>
                <div class="text-xl">
                  Healthy
                </div>
              </div>
              <div class="highlights-card">
                <div class="text-xl text-slate-400">
                  Air Quality
                </div>
                <div class="text-5xl font-semibold">
                  105
                </div>
                <div class="text-xl">
                  Unhealthy
                </div>
              </div>
              <div class="highlights-card">
                <div class="text-xl text-slate-400">
                  Sunrise & Sunset
                </div>
                <div class="flex gap-6">
                  <img class="h-14" src="../assets/img/arrowUp.jpg">
                  <div>
                    <div class="font-semibold text-xl">6:35 AM</div>
                    <div class="font-semibold text-sm text-slate-400">-1m 46s</div>
                  </div>
                </div>
                <div class="flex gap-6">
                  <img class="h-14 rotate-180" src="../assets/img/arrowUp.jpg">
                  <div>
                    <div class="font-semibold text-xl">5:42 PM</div>
                    <div class="font-semibold text-sm text-slate-400">-2m 22s</div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <table class="lg:hidden bg-white font-semibold overflow-hidden shadow-none rounded-2xl alight-left text-lg bg-content">
            <tr class="text-slate-400  text-xl">
              <td>Day</td>
              <td><img class="inline h-5 mr-2" src="../assets/icons/termometr.png">t°</td>
              <td><img class="inline h-5 mr-2" src="../assets/icons/rain-icon.png">Rain</td>
              <td><img class="inline h-5 mr-2" src="../assets/icons/wind-small.png">Wind</td>
            </tr>
            <tr>
              <td>Воскресенье<div class="block">29 октября</div></td>
              <td>9°C</td>
              <td>20</td>
              <td>3 м/с</td>
            </tr>
            <tr>
              <td>Воскресенье<div class="block">29 октября</div></td>
              <td>9°C</td>
              <td>20</td>
              <td>3 м/с</td>
            </tr>
            <tr>
              <td>Воскресенье<div class="block">29 октября</div></td>
              <td>9°C</td>
              <td>20</td>
              <td>3 м/с</td>
            </tr>
            <tr>
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
import dayjs from "dayjs"

export default {
  name: "MainPage",
  data () {
    return {
      weather: '',
      userCity: '',

    }
  },
  methods: {
     async fetchWeather() {
         await fetch('../mock/forecast.json', {
         headers: {
           'Content-Type': 'application/json',
           'Accept': 'application/json'
         }
       })
         .then(res => res.json())
         .then(json => this.weather = json)
      console.log(this.weather,'weather')
    },
    kelvinToCelsius(temp) {
      return Math.round(temp - 273.15).toString()
    },
    GetCurrentDay() {
       return new Date().toLocaleString("en-US", { weekday: "long" })
    },
    GetCurrentDayShort(n) {
      return  (dayjs().weekday(dayjs().day() + n).$d).toString().substring(0,4)
    },

  },
  mounted() {
    dayjs.extend(weekday)
    this.fetchWeather()
    console.log(dayjs().weekday(dayjs().day() + 1).$d,'!!!!!!')

  }
}

</script>

<style scoped>

  div {
  }

  .progress{
    position: relative;
    margin: 4px;
    float:left;
    text-align: center;
  }
  .barOverflow{
    position: relative;
    width: 180px; height: 90px;
    margin-bottom: -16px;
    overflow: hidden;
  }
  .bar {
    position: absolute;
    top: 0; left: 0;
    width: 180px; height: 180px;
    border-radius: 50%;
    box-sizing: border-box;
    border: 20px solid rgb(226 232 240);
    border-bottom-color: #ffb433;
    rotate: 120deg;
  }
  tr td {
    padding: 10px;

  }

</style>