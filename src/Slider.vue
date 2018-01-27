<template>
    <div class="slider">
        <vue-slider
                v-model="value"
                :interval="interval"
                :dotWidth="dotWidth"
                :dotHeight="dotHeight"
                :formatter="formatter"
                :bgStyle="bgStyle"
                :processStyle="processStyle"
                :tooltipStyle="tooltipStyle"

                :min="min"
                :max="max"

                ></vue-slider>

        <div>
            <div>Show value</div>
            <div>
                {{value}}
            </div>
            <div>{{viewValue()}}</div>
        </div>
    </div>
</template>
<script>
    /*




    * */
    import vueSlider from 'vue-slider-component';

    export default {
        components: {
            vueSlider
        },
        data () {
            return {
                value: 45,
                min: 10,
                max: 80,

                dotWidth: 24,
                dotHeight: 16,
                formatter: "{value} Гб",
                interval: 1,

                width: "400px",
                    height: 60,
                    direction: "horizontal",
                    clickable: true,

                bgStyle: {
                        "backgroundColor": "#fff",
                    "boxShadow": "inset 0.5px 0.5px 3px 1px rgba(0,0,0,.36)"
                },
                processStyle: {
                    "backgroundColor": "#B44536",
//                    "backgroundImage": "-webkit-linear-gradient(left, #f05b72, #3498db)"
                },
                tooltipStyle: [
                    {
                        "backgroundColor": "#cc0000",
                        "borderColor": "#cc0000"
                    },
                    {
                        "backgroundColor": "#ccc",
                        "borderColor": "#ccc"
                    }
                ]

            }
        },
        methods:{
            viewValue(){
                this.$emit("viewValueApp",this.value+1000    )

//                this.temp = this.sliderInfo.value;
                return this.value+1000;
//                return 5566;
            },
        }

    }
</script>


<style>
    div.slider{
        width:200px;
    }
</style>