<template>
    <div class="custom-settings">
        <div class="custom-settings__title ">Настраиваемые параметры</div>

      <!--  <div class="custom-settings__item">
            <div class="custom-settings__name ">Количество CPU</div>
            <div class="custom-settings__slider "><div class="custom-settings__slider_fill "></div></div>
            <div class="custom-settings__slider-info ">
                <div class="custom-settings__slider-info-num">12</div>
            </div>
        </div>-->

    <!--    <div class="custom-settings__item">
            <div class="custom-settings__name ">Количество CPU</div>
            <div class="custom-settings__slider "><div class="custom-settings__slider_fill "></div></div>
            <div class="custom-settings__slider-info ">
                <div class="custom-settings__slider-info-num">12</div>
            </div>
        </div>-->

            <slider-s
                    v-for="(sliderI, ii) in sliders"
                    :keykey="ii+1"
                    :sliderInfo="sliderI"
                    @valueSlidersIn="valueSliders"
                    @checkSettingIn="checkSetting"
            ></slider-s>
        <!--<hr>-->
        <!--<div>{{dataSliders}}</div>-->
        <!--<hr>-->
        <hr>
        <div>selectedSolutionIn</div>
        <!--<div>{{selectedSolutionIn}}</div>-->
        <!--<div>{{changeValue}}</div>-->
        <hr>


        <div class="hide" style="display:none1">
            {{changeValue}}
            {{sumSolution()}}
            <!--{{sumSelected()}}-->
            <div>tempSelectSolution - {{tempSelectSolution}}</div>
            <div>selectedSolutionIn - {{selectedSolutionIn}}</div>

        </div>
    </div>

</template>

<script>

//    import vueSlider from 'vue-slider-component';
    import slider_s from './Slider_s.vue'

    export default {
        props:{
//            selectedSolutionIn: {
////                type: Number,
//                required: true,
//            },
            selectedSolutionIn: {
//                type: Number,
                required: true,
            }

        },
        components: {
        'slider-s': slider_s
        },
        data(){
            return {
                sliders: [
                    {
                        name: 'Количество CPU',
                        value: 4,
                        formatter: "{value} шт",
                        min: 1,
                        max: 32,
                        interval: 1,
                        price: 200,


                    },
                    {
                        name: 'Объем RAM',
                        value: 8,
                        formatter: "{value} Гб",
                        min: 2,
                        max: 128,
                        interval: 2,
                        price: 300,

                    },
                    {
                        name: 'Место на диске HDD',
                        value: 10,
                        formatter: "{value} Тб",
                        min: 1,
                        max: 100,
                        interval: 1,
                        price: 450,

                    },
                    {
                        name: 'Место на диске SSD',
                        value: 50,
                        formatter: "{value} Гб",
                        min: 2,
                        max: 512,
                        interval: 2,
                        price: 50,

                    },
                    {
                        name: 'Backup',
                        value: 166,
                        formatter: "{value} Гб",
                        min: 2,
                        max: 2024,
                        interval: 2,
                        price: 20,

                    },
                ],
                dataSliders: {
                    1: 0,
                    2: 0,
                    3: 0,
                    4: 0,
                    5: 0,
                },
//                changeValue:{},
                resetS:{},
                garantPrice: 0,
                sumSolutionSelect: 0,
                sumSelectedVal: 0,
                tempSelectSolution: 0,
            }
        },
        computed: {
            changeValue(){


                if(this.tempSelectSolution  !=this.selectedSolutionIn){
                    console.log("here_0");

                    this.tempSelectSolution = this.selectedSolutionIn;




    //                return 1+7;
    //                console.log(this.selectedSolutionIn);
                    if (this.selectedSolutionIn == 1) {

                        this.sliders[0].value = 4;
                        this.sliders[1].value = 10;
                        this.sliders[2].value = 4;
                        this.sliders[3].value = 100;
                        this.sliders[4].value = 10;
                        console.log("here1");

                    }
                      else



                     if (this.selectedSolutionIn == 2) {
    //                    console.log("00000");
                        this.sliders[0].value = 16;
                        this.sliders[1].value = 50;
                        this.sliders[2].value = 16;
                        this.sliders[3].value = 200;
                        this.sliders[4].value = 100;
                         console.log("here2");

                    }
                    else if (this.selectedSolutionIn == 3) {
    //                    console.log("00000");
                        this.sliders[0].value = 30;
                        this.sliders[1].value = 100;
                        this.sliders[2].value = 60;
                        this.sliders[3].value = 400;
                        this.sliders[4].value = 1000;
                         console.log("here3");
                     }
                    if(this.selectedSolutionIn){
                        this.sumSolutionSelect = sumSolution(this.sliders);
    //                    console.log("here2");
                    }

                }
                this.sumSelectedVal = sumSolution(this.sliders);

            },

        },
        methods: {
            checkSetting(id){
//                console.log("0 checkSetting methods 000____" + id);
//                console.log(id-1 + "_++__" +this.sliders[id-1].value);
//                this.resetS = true;
//                this.$emit("resetSolution",this.resetS);


//                console.log(this.sliders);
//
//                let sumSelected = sumSolution(this.sliders);
//                this.$emit("sumSelected", sumSelected)
            },
            valueSliders(vals){
                this.sliders[vals.id-1].value = vals.value;

//                console.log("valueSliders===" + vals.value);


//                this.sumSelected = sumSolution(this.sliders);
//
//                console.log(this.sumSelected);


                this.dataSliders[vals.id] = vals.value;


                this.$emit("valueSliders",this.dataSliders);


            },
            sumSolution(){
//                console.log(this.sliders);
                this.$emit("sumSolution", this.sumSolutionSelect);
                this.$emit("sumSelected", this.sumSelectedVal);
            },/*
            sumSelected(){
//                console.log("99999999999");
//                let sumSelected = sumSolution(this.sliders);
                this.$emit("sumSelected", this.sumSelected)
            }*/

//            valueSlider

        }
    }

    function sumSolution(Arr){

        let sum=0;
        for(let i=0;i<Arr.length;i++){
    //        console.log(Arr[i].value);
    //        console.log(parseInt(Arr[i].value) * parseInt(Arr[i].price));
            sum = sum + (parseInt(Arr[i].value) * parseInt(Arr[i].price));

        }

    //    console.log(sum);
        return sum;

    }
</script>

<style>

    .custom-settings{}
    .custom-settings__title{
        margin-bottom:20px;
    }


</style>