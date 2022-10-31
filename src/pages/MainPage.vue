<template>
  <div class="min-h-screen flex flex-col h-1 bg-gray"> <!--  вся ширина-->
    <div class="container my-10 px-1 mx-auto h-full">
      <div class="flex flex-col h-full lg:flex-row">
        <div
          class="gap-4 bg-white h-full font-semibold flex flex-col p-2
          items-center rounded-t-[56px] lg:p-6 lg:rounded-l-[56px] lg:rounded-tr-none"
        >
         <div class="h-3/4">
           <div class="flex items-center">
             <img class="h-5" src="../assets/icons/search-icon.png">
             <input
               type="text"
               class="w-full max-w-[240px] text-black outline-0 rounded-xl p-1"
               placeholder="Search for places..."
             >
           </div>
           <img class="h-40 lg:h-56" src="../assets/icons/weather-state1.png">
           <div class="text-6xl font-normal lg:text-8xl lg:self-start">12<sup class="text-4xl">°C</sup></div>
           <div class="text-xl font-normal lg:text-3xl lg:self-start">Monday</div>
         </div>


          <hr class="hr-line">
          <div class="h-1/2">
            <div class="flex flex-col w-full justify-between lg:justify-around h-full ">
              <div class="h-12 flex items-center lg:text-2xl gap-4"><img class="inline" height="32" width="32" src="../assets/icons/rain-small.png">Rain 30%</div>
              <div class="h-12 flex items-center lg:text-2xl gap-4"><img class="inline" height="32" width="32" src="../assets/icons/cloud-Icon.png">Mostly Cloudy</div>
              <div class="text-2xl  lg:h-20 p-4  rounded-xl text-white z-10 bg-center bg-cover text-center relative lg:text-3xl"> <img class="h-full -m-4 rounded-xl w-full absolute -z-10" src="https://img5.goodfon.ru/original/2048x1284/4/68/nyc-skyline-new-york-in-blue.jpg"> Россия,Москва</div>
            </div>
          </div>

        </div>
        <div class="flex flex-col p-2 w-full bg-content rounded-b-[56px] lg:rounded-bl-none lg:rounded-r-[56px]">
          <div class="h-64 mt-12 hidden gap-4 lg:flex flex-col lg:flex-row">
            <div class="w-full lg:hidden rounded-xl text-gray-400 flex lg:flex-row justify-between bg-white p-1">
              <div>День</div>
              <div>T</div>
              <div>Осадки</div>
              <div>Ветер</div>
            </div>
            <div class="w-full flex flex-col justify-between bg-white h-[186px] rounded-2xl p-4 items-center">
              <div>Воскресенье</div>
              <div>9°C</div>
              <div>20%</div>
              <div>3 м/с</div>
            </div>
            <div class="w-full flex lg:flex-col justify-between bg-white p-1">
              <div>Воскресенье</div>
              <div>9°C</div>
              <div>20%</div>
              <div>3 м/с</div>
            </div>
            <div class="w-full flex lg:flex-col justify-between bg-white p-1">
              <div>Воскресенье</div>
              <div>9°C</div>
              <div>20%</div>
              <div>3 м/с</div>
            </div>
            <div class="w-full flex lg:flex-col justify-between bg-white p-1">
              <div>Воскресенье</div>
              <div>9°C</div>
              <div>20%</div>
              <div>3 м/с</div>
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


export default {
  name: "MainPage"
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