<template>
    <div class="custom-settings">
        <div class="custom-settings__title ">Настраиваемые параметры</div>
            <slider-s
                    v-for="(sliderI, ii) in sliders"
                    :keykey="ii+1"
                    :sliderInfo="sliderI"
                    @valueSlidersIn="valueSliders"
                    @checkSettingIn="checkSetting"
            ></slider-s>

        <div class="hide" style="display:none">
            {{changeValue}}
            {{sumSolution()}}

        </div>
    </div>

</template>

<script>

    import slider_s from './Slider_s.vue'

    export default {
        props:{
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
                resetS:{},
                garantPrice: 0,
                sumSolutionSelect: 0,
                sumSelectedVal: 0,
                tempSelectSolution: 0,
            }
        },
        computed: {
            changeValue(){


                if (this.tempSelectSolution != this.selectedSolutionIn) {
                    console.log("here_0");

                    this.tempSelectSolution = this.selectedSolutionIn;
                    if (this.selectedSolutionIn == 1) {

                        this.sliders[0].value = 4;
                        this.sliders[1].value = 10;
                        this.sliders[2].value = 4;
                        this.sliders[3].value = 100;
                        this.sliders[4].value = 10;
                    }
                    else if (this.selectedSolutionIn == 2) {
                        this.sliders[0].value = 16;
                        this.sliders[1].value = 50;
                        this.sliders[2].value = 16;
                        this.sliders[3].value = 200;
                        this.sliders[4].value = 100;
                    }
                    else if (this.selectedSolutionIn == 3) {
                        this.sliders[0].value = 30;
                        this.sliders[1].value = 100;
                        this.sliders[2].value = 60;
                        this.sliders[3].value = 400;
                        this.sliders[4].value = 1000;
                    }
                    else if (this.selectedSolutionIn == 4) {
                        this.sliders[0].value = 30;
                        this.sliders[1].value = 100;
                        this.sliders[2].value = 100;
                        this.sliders[3].value = 500;
                        this.sliders[4].value = 2000;
                    }
                    if (this.selectedSolutionIn) {
                        this.sumSolutionSelect = sumSolution(this.sliders);
                    }

                }
                this.sumSelectedVal = sumSolution(this.sliders);

            },

        },
        methods: {
            checkSetting(id){
            },
            valueSliders(vals){
                this.sliders[vals.id-1].value = vals.value;


                this.dataSliders[vals.id] = vals.value;


                this.$emit("valueSliders",this.dataSliders);


            },
            sumSolution(){
                this.$emit("sumSolution", this.sumSolutionSelect);
                this.$emit("sumSelected", this.sumSelectedVal);
            },
        }
    }

    function sumSolution(Arr){

        let sum=0;
        for(let i=0;i<Arr.length;i++){
            sum = sum + (parseInt(Arr[i].value) * parseInt(Arr[i].price));
        }
        return sum;
    }
</script>

<style>

    .custom-settings{}
    .custom-settings__title{
        margin-bottom:20px;
    }


</style>