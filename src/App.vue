<template>

<div class=" mts-configurator">
    <!--<img src="./assets/logo.png">-->

      <div class="mts-configurator__title ">Конфигуратор Инфраструктуры</div>


      <block-Solution
              @selectedSolutionIn="selectedSolutionApp"
              @clickSolutionIn="selectedClickSolutionApp"
      ></block-Solution>

      <block-custom-setting
              @valueSliders="blockCustomSetting"
              :selectedSolutionIn="selectedSolution"
              :selectedClickSolutionAppIn="selectedClickSolutionApp"
              @sumSolution="sumSolution"
              @sumSelected="sumSelected"
      ></block-custom-setting>



      <block-Services @selectedLicense="selectedLicense"></block-Services>


      <div>SumSolutionReturn --- {{sumSolutionSelected}}</div>
      <div>sumSelectedSelectedReturn --- {{sumSelectedSelected}}</div>
      <div>selectedLicenses --- {{selectedLicenses}}</div>
      --------


      <block-Tariff :tariff1="tariff1" :tariff2="tariff2"></block-Tariff>
</div>
</template>

<script>




    import slider from './Slider.vue';
import blockCustomSetting from './CustomSetting/CustomSetting.vue';
import blockSolution from './Solution/Solution.vue';
import blockServices from './Services/Services.vue';
import blockTariff from './Tariff/Tariff.vue';

export default {
  name: 'app',
  data () {
    return {

        dataSliders: {},
        selectedSolution:0,
        selectedLicenses:0,
        sumSolutionSelected:0,
        sumSelectedSelected:0,

    }
  },
    components: {
        slider,
        blockCustomSetting,
        blockSolution,
        blockServices,
        blockTariff,
    },
    computed: {
      tariff1(){
          if(this.selectedSolution){
              return this.selectedLicenses + this.sumSolutionSelected;
          }else{
              return 0;
          }
      },
      tariff2(){
          return this.selectedLicenses + this.sumSelectedSelected;
      },

    },
    methods:{
        viewOneSlider(oneVal){
            this.tempView = oneVal;
        },
        blockCustomSetting(dataS){
            this.dataSliders = dataS;
        },
        selectedSolutionApp(id){
            this.selectedSolution = id;
        },
        selectedClickSolutionApp(id){
            console.log(id);
            this.selectedSolution = id;
        },
        selectedLicense(sumLicenses){
            this.selectedLicenses = sumLicenses;
        },
        sumSolution(Sum){
            this.sumSolutionSelected = Sum;
        },
        sumSelected(Sum){
            this.sumSelectedSelected = Sum;
        }

    }
}
</script>

<style>
    .mts-configurator{
        margin:0 auto;
        border:  2px dotted #ccc;
        border-radius: 10px;
        width: 1000px;
        text-align:center;
        background: #FAFAFA;
        padding-top:30px;
    }
    .mts-configurator > div{
        margin-bottom:50px;
    }



    .hide{
        /*display:none1;*/
    }
</style>
