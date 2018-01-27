<template>
  <div id="app">
    <!--<img src="./assets/logo.png">-->
    <h1>{{ msg }}</h1>
    <!--<slider-->
            <!--@viewValueApp="viewOneSlider"-->

    <!--&gt;</slider>-->
      <hr>

      <block-Solution @selectedSolutionIn="selectedSolutionApp"></block-Solution>
      <br>
      <!--==={{selectedSolution}}===-->
      <br>
      <br>
      <!--<slider-s
              v-for="(sliderI, ii) in sliders"
              :keykey="ii+1"
              :sliderInfo="sliderI"
      ></slider-s>-->

      <block-custom-setting @valueSliders="blockCustomSetting" :selectedSolutionIn="selectedSolution"></block-custom-setting>

      <div>
          <br>
          <br>
          <div>инфо App.vue</div>
          <!--<div>{{tempView}}</div>-->
          <!--<div>{{tempInfo}}</div>-->
          <div>{{dataSliders}}</div>
      </div>
  </div>
</template>

<script>


//    @viewValue="sliderValue"
//<div>{{sliderValue()}}</div>
/*




 <div>{{viewOneSlider()}}</div>
*
* */

    import slider from './Slider.vue';
//import slider_s from './Slider_s_0.vue'
import blockCustomSetting from './CustomSetting/CustomSetting.vue';
import blockSolution from './Solution/Solution.vue';

export default {
  name: 'app',
  data () {
    return {
        tempView: {},
        tempInfo: {
            x: 33,
            y: 23,
            z: 99,
            name: "234",
        },
        msg: 'Welcome to Your Vue.js App',
        /*sliders: [
            {
                name: 'Количество CPU',
                value: 4,
                formatter: "{value} шт",
                min: 1,
                max: 32,
                interval: 1,


            },
            {
                name: 'Объем RAM',
                value: 8,
                formatter: "{value} Гб",
                min: 2,
                max: 128,
                interval: 2,

            },
            {
                name: 'Место на диске HDD',
                value: 10,
                formatter: "{value} Тб",
                min: 1,
                max: 100,
                interval: 1,

            },
            {
                name: 'Место на диске SSD',
                value: 50,
                formatter: "{value} Гб",
                min: 2,
                max: 512,
                interval: 2,

            },
            {
                name: 'Backup',
                value: 166,
                formatter: "{value} Гб",
                min: 2,
                max: 2024,
                interval: 2,

            },
        ]*/
        dataSliders: {},
        selectedSolution:{},

    }
  },
    components: {
        slider,
//        'slider-s': slider_s
        blockCustomSetting,
        blockSolution,
    },
    methods:{
//        sliderValue(val){
//            return val;
//        }
        viewOneSlider(oneVal){
//        viewOneSlider(){
            this.tempView = oneVal;
//            return oneVal;
//            return 9999;
        },
        blockCustomSetting(dataS){
            this.dataSliders = dataS;
        },
        selectedSolutionApp(id){
//            console.log(id);
            this.selectedSolution = id;
        }
    }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
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
</style>
