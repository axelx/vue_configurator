<template>

    <!--  <div class="custom-settings__item">
      <div class="custom-settings__name ">Количество CPU</div>
      <div class="custom-settings__slider "><div class="custom-settings__slider_fill "></div></div>
      <div class="custom-settings__slider-info ">
          <div class="custom-settings__slider-info-num">12</div>
      </div>
  </div>-->


        <div class="custom-settings__item">
            <div class="custom-settings__name ">{{sliderInfo.name}}</div>

            <vue-slider
                    v-model="sliderInfo.value"

                    :min="sliderInfo.min"
                    :max="sliderInfo.max"
                    :interval="sliderInfo.interval"
                    :formatter="sliderInfo.formatter"

                    :processStyle="processStyle"
                    :tooltipStyle="tooltipStyle"
                    @click.native="checkSetting(keykey)"

            ></vue-slider>
            <div>
                {{viewValue()}}

            </div>
      <!--      <div>==================</div>
            <div>{{valueSelected}}</div>
            <div>==================</div>-->

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
            checkSetting(){
//                console.log("++00111");
//                console.log(this.keykey);
                this.$emit("checkSettingIn", this.keykey);
            },
            viewValue(){
//                for(var ii = 0, ii <=)
                this.valueSelected[this.keykey] = this.sliderInfo.value;
//                return "0900909";



//                let valUp = {};
//
//                valUp[this.keykey] = this.sliderInfo.value;

                this.$emit("valueSlidersIn",{
                    id : this.keykey,
                    value : this.sliderInfo.value,
                    name : this.sliderInfo.name,
                });

//                this.temp = this.sliderInfo.value;
                return this.keykey + "   ____   " + this.sliderInfo.value;
            },
        }

    }
</script>


<style>
/*
    div.slider{
        width:200px;
        display:inline-block;
        margin:10px;
    }
*/



    .custom-settings__item{
        display:inline-block;
        width:190px;

    }
    .custom-settings__name{
        font-size:14px;
        color: #2e3e25;
        margin-bottom: 30px;

    }
    .custom-settings__slider{
        background: #c7c7c7;
        width:100%;
    }
    .custom-settings__slider_fill{
        background: #B44536;
        width:40%;
        height:4px;
    }
    .custom-settings__slider-info{
        background: #B44536;
        border-radius: 10px;
        width: 58px;
        margin: 0 auto;
        position: relative;
        bottom: 14px;
    }
    .custom-settings__slider-info:hover{
        cursor: pointer;
    }

    .custom-settings__slider-info-num{
        color:white;
        padding:3px 5px;

    }
</style>