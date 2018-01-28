<template>

    <!--<div class="solution__item solution__item_active">Medium</div>-->

<!--
    <div class="solution">
        <div class="solution__title ">Готовые решения</div>
        <div class="solution__item ">Small</div>
        <div class="solution__item solution__item_active">Medium</div>
        <div class="solution__item ">Large</div>
    </div>-->
    <div class="solution"
         @click=" clickSolution"
    >
        <div class="solution__title ">Готовые решения</div>
        <div class="solution__item "
             v-for="(solution) in solutions"
             :key="solution.id"
             @click.prevent="activeItem = solution.id"
             :class="{ solution__item_active: activeItem === solution.id}"
        >{{solution.name}}</div>


        <!--<hr>-->
        {{selectedSolution()}}
        <!--<div class="hide" style="1display:1none">-->
        <!--</div>-->
    </div>
</template>



<script>

    /*

     @click="selectSolution(solution.id)"


     */



//    import vueSlider from 'vue-slider-component';

    export default {
        components: {
//            vueSlider
        },
        props:{
//            keykey: {
//                type: Number,
//                required: true,
//            },
//            sliderInfo:{
//                type:Object,
//                required: true
//            }
        },
        data () {
            return {

                activeSolution: 1,
                solutions: [
                    {
                        id: 1,
                        name: 'Small',
                    },
                    {
                        id: 2,
                        name: 'Medium',
                    },
                    {
                        id: 3,
                        name: 'Large',
                    },
                ],
                activeItem: null,

            }
        },
        methods:{
            selectedSolution(){
                this.$emit("selectedSolutionIn",this.activeItem);
                return this.activeItem;

            },
            clickSolution(){
                console.log("===clickSolution======= " + this.activeItem);
                this.$emit("clickSolutionIn",this.activeItem);
//                return this.activeItem;

            },
        }

    }
</script>


<style>
    .active:after {
        content: '< active';
        color: red;
    }


    /*solution*/
    .solution{}
    .solution__title{}
    .solution__item{
        display:inline-block;
        border:1px solid #B44536;
        border-radius: 5px;
        padding:15px 5px;
        width:70px;
    }
    .solution__item_active{
        color:white;
        background: #B44536;
    }
    .solution__item:hover{
        cursor:pointer;
        /*background: #ccc;*/
        opacity:0.7;
    }
</style>