<template>
  <div v-if="weather !== ''" class="min-h-screen flex flex-col bg-gray px-2"> <!--  вся ширина-->
    <div class="container my-12 px-1 max-w-[1280px] mx-auto">
      <div class="flex flex-col lg:flex-row">
        <div class="gap-4 bg-white flex flex-col p-2 lg:w-[40%]
           rounded-t-[56px] lg:justify-between lg:p-11 lg:rounded-l-[56px] lg:rounded-tr-none"
        >
          <div class="flex items-center self-center gap-2">
            <img class="h-5 " src="../assets/icons/search-icon.png">
            <input
              class="w-full max-w-[240px] pl-4 focus:bg-gray-200 rounded-2xl py-2 px-1 font-medium"
              placeholder="Search for places..."
            >
        </div>
          <div class="flex lg:flex-col flex-row justify-center">
           <img
             class="lg:mt-6 lg:h-[300px] h-32"
             src="../assets/icons/weather-state1.png">
           <div class="mt-10">
             <div class="text-6xl flex lg:text-8xl">{{kelvinToCelsius(this.weather.list[0].main.temp)}}
               <span class="text-6xl relative top-[6px]">°C</span>
             </div>
             <div class="text-xl my-8 lg:text-3xl">{{GetCurrentDay()}}</div>
           </div>
          </div>
          <hr class="hr-line">
          <div class="w-full">
            <div class="flex lg:flex-col h-full flex-row justify-around lg:justify-between">
              <div>
                <div class="h-12 text-sm lg:text-base capitalize flex items-center gap-4">
                  <img width="32" src="../assets/icons/cloud-Icon.png">{{weather.list[0].weather[0].description}}
                </div>
                <div class="h-12 flex items-center text-sm lg:text-base gap-4">
                  <img width="32" src="../assets/icons/rain-small.png">Rain
                  {{weather.list[0].main.humidity}}%
                </div>
              </div>
              <div
                class="text-xl flex items-center justify-center
                lg:mt-10 p-8 rounded-xl text-white z-10 bg-center bg-cover relative lg:text-2xl">
                <img
                  class="h-full shadow-xl rounded-2xl lg:w-full absolute -z-10"
                  src="../assets/img/city-bg.jpg"
                >
                <div class="bg-black absolute h-full -z-10 opacity-30 rounded-2xl w-full"> </div>
                {{weather.city.country}},{{weather.city.name}}
              </div>
            </div>
          </div>
        </div>
        <div class="flex flex-col p-4 lg:p-11 w-full bg-content rounded-b-[46px] lg:rounded-bl-none lg:rounded-r-[46px]">
          <div class="lg:flex justify-between font-semibold text-slate-400 text-2xl hidden">
            <div>
              <span class="hover:text-black">Today</span>
              <span class="text-black underline pl-6 underline-offset-8">Week</span>
            </div>
            <div class="text-2xl flex items-center gap-4">
              <span class="px-3 py-2 bg-black rounded-full text-white">°C</span>
              <span class="text-black px-3 py-2 bg-white rounded-full">°F</span>
              <img class="w-14 h-14 ml-8 rounded-xl" src="../assets/img/avatar.jpeg">
            </div>
          </div>
          <div class="mt-20 hidden gap-1l lg:grid gap-2 lg:grid-cols-[repeat(7,minmax(100px,_1fr))]">
            <div class="weeks-day-card">
              <div class="font-medium">{{GetCurrentDayShort(1)}}</div>
              <img class="h-12" src="../assets/icons/weather-state1.png">
              <div><span>{{kelvinToCelsius(weather.list[6].main.temp)}}°C</span></div>
            </div>
            <div class="weeks-day-card">
              <div class="font-medium">{{GetCurrentDayShort(2)}}</div>
              <img class="h-12" src="../assets/icons/weather-state1.png">
              <div>{{kelvinToCelsius(weather.list[14].main.temp)}}°C</div>
            </div>
            <div class="weeks-day-card">
              <div class="font-medium">{{GetCurrentDayShort(3)}}</div>
              <img class="h-12" src="../assets/icons/weather-state1.png">
              <div>{{kelvinToCelsius(weather.list[22].main.temp)}}°C</div>
            </div>
            <div class="weeks-day-card">
              <div class="font-medium">{{GetCurrentDayShort(4)}}</div>
              <img class="h-12" src="../assets/icons/weather-state1.png">
              <div>{{kelvinToCelsius(weather.list[29].main.temp)}}°C</div>
            </div>
            <div class="weeks-day-card">
              <div class="font-medium">{{GetCurrentDayShort(5)}}</div>
              <img class="h-12" src="../assets/icons/weather-state1.png">
              <div>{{kelvinToCelsius(weather.list[36].main.temp)}}°C</div>
            </div>
            <div class="weeks-day-card">
              <div class="font-medium">{{GetCurrentDayShort(6)}}</div>
              <img class="h-12" src="../assets/icons/weather-state1.png">
              <div>{{kelvinToCelsius(weather.list[36].main.temp)}}°C</div>
            </div>
            <div class="weeks-day-card">
            <div class="font-medium">{{GetCurrentDayShort(7)}}</div>
            <img class="h-12" src="../assets/icons/weather-state1.png">
            <div>{{kelvinToCelsius(weather.list[36].main.temp)}}°C</div>
          </div>
          </div>
          <div class="hidden lg:flex h-full lg:mt-28 xl:mt-14 flex-col lg:justify-end gap-10">
            <div class="font-semibold text-4xl">Today's Highlights</div>
            <div class="grid lg:grid-cols-2 xl:grid-cols-3 xl:auto-rows-[224px] content-end  gap-4">
              <div class="highlights-card">
                <div class="text-xl text-slate-400">Humidity</div>
                <div class="text-5xl font-medium">{{weather.list[0].main.humidity}}%</div>
                <div class="text-xl">Normal</div>
              </div>
              <div class="lg:gap-6 xl:gap-0 highlights-card">
                <div class="text-xl text-slate-400">
                  UV index
                </div>
                <div>
                  <div class="relative flex w-[200px] top-[32px] mx-auto justify-center">
                    <div class="progress">
                      <div class="barOverflow">
                        <div class="bar"></div>
                      </div>
                      <span class="text-5xl relative bottom-[30px]">5</span>
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
                <div class="text-5xl font-medium">
                  {{weather.list[0].wind.speed}}%
                </div>
                <div class="text-xl">
                  WSW
                </div>
              </div>
              <div class="highlights-card">
                <div class="text-xl text-slate-400">
                  Visibility
                </div>
                <div class="text-5xl font-medium">
                  {{weather.list[0].visibility}}M
                </div>
                <div class="text-xl">
                  Healthy
                </div>
              </div>
              <div class="highlights-card">
                <div class="text-xl text-slate-400">
                  Air Quality
                </div>
                <div class="text-5xl font-medium">
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
                    <div class="font-medium text-xl">6:35 AM</div>
                    <div class="font-medium text-sm text-slate-400">-1m 46s</div>
                  </div>
                </div>
                <div class="flex gap-6">
                  <img class="h-14 rotate-180" src="../assets/img/arrowUp.jpg">
                  <div>
                    <div class="font-medium text-xl">5:42 PM</div>
                    <div class="font-medium text-sm text-slate-400">-2m 22s</div>
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