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
                    @valueSliders="valueSliders"
            ></slider-s>
        <!--<hr>-->
        <!--<div>{{dataSliders}}</div>-->
        <!--<hr>-->
        <hr>
        <div>selectedSolutionIn</div>
        <!--<div>{{selectedSolutionIn}}</div>-->
        <!--<div>{{changeValue}}</div>-->
        <hr>


        <div class="hide" style="display:none">
            {{changeValue}}

        </div>
    </div>

</template>

<script>

//    import vueSlider from 'vue-slider-component';
    import slider_s from './Slider_s.vue'

    export default {
        props:{
            selectedSolutionIn: {
//                type: Number,
                required: true,
            },

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
                ],
                dataSliders: {
                    1: 0,
                    2: 0,
                    3: 0,
                    4: 0,
                    5: 0,
                },
//                changeValue:{},
            }
        },
        computed: {
            changeValue(){
//                return 1+7;
                if (this.selectedSolutionIn == 1) {
//                    console.log("00000");
                    this.sliders[0].value = 4;
                    this.sliders[1].value = 10;
                    this.sliders[2].value = 4;
                    this.sliders[3].value = 100;
                    this.sliders[4].value = 10;
                }
                else if (this.selectedSolutionIn == 2) {
//                    console.log("00000");
                    this.sliders[0].value = 16;
                    this.sliders[1].value = 50;
                    this.sliders[2].value = 16;
                    this.sliders[3].value = 200;
                    this.sliders[4].value = 100;
                }
                else if (this.selectedSolutionIn == 3) {
//                    console.log("00000");
                    this.sliders[0].value = 30;
                    this.sliders[1].value = 100;
                    this.sliders[2].value = 60;
                    this.sliders[3].value = 400;
                    this.sliders[4].value = 1000;
                }

            },

        },
        methods: {
            valueSliders(vals){
                this.dataSliders[vals.id] = vals.value;

                this.$emit("valueSliders",this.dataSliders);
            },
//            valueSlider

        }
    }


</script>

<style>

    .custom-settings{}
    .custom-settings__title{
        margin-bottom:20px;
    }


</style>