<template>
    <div class="slider">
        <div>
            <!--<div>Имя слайдера</div>-->
            <div>{{sliderInfo.name}}</div>
            <br><br><br>
        </div>
        <vue-slider
                v-model="sliderInfo.value"

                :min="sliderInfo.min"
                :max="sliderInfo.max"
                :interval="sliderInfo.interval"
                :formatter="sliderInfo.formatter"

                :processStyle="processStyle"
                :tooltipStyle="tooltipStyle"

        ></vue-slider>

        <div>
            <div>Show value</div>
            <div>
                {{sliderInfo.value}}
            </div>
            <div>
                {{viewValue()}}
            </div>
        </div>
    </div>
</template>
<script>
    import vueSlider from 'vue-slider-component';

    export default {
        components: {
            vueSlider
        },
        props:{
            keykey: {
                type: Number,
                required: true,
            },
            sliderInfo:{
                type:Object,
                required: true
            }
        },
        data () {
            return {

                processStyle: {
                    "backgroundColor": "#B44536",
//                    "backgroundImage": "-webkit-linear-gradient(left, #f05b72, #3498db)"
                },
                tooltipStyle: [
                    {
                        "backgroundColor": "#000",
                        "borderColor": "#000"
                    },
                    {
                        "backgroundColor": "#B44536",
                        "borderColor": "#B44536"
                    }
                ],
                temp: "111",
                valueSelected:{},
            }
        },
        methods:{
            viewValue(){
//                this.$emit("viewValue",this.sliderInfo.value    )

//                this.temp = this.sliderInfo.value;
                return this.keykey + "   _1___   " + this.sliderInfo.value;
            },
        }

    }
</script>


<style>
    div.slider{
        width:200px;
        display:inline-block;
        margin:10px;
    }
</style>