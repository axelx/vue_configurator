<template>
    <div>

        <div class="tariff">
            <div class="tariff__title">Тарифы</div>
            <div class="tariff__item"
                 @click.prevent="activeItem = 1"
                 :class="{ tariff__item_active: activeItem === 1}"
            >
                <div class="tariff__name">Гарантированный</div>
                <div class="tariff__price tariff__price-rub">{{resTariff(tariff1)}} <span class="rub rub_25 rub_black">Р</span></div>
                <div class="tariff__description">в месяц</div>
            </div>

            <div class="tariff__item"
                 @click.prevent="activeItem = 2"
                 :class="{ tariff__item_active: activeItem === 2}"
            >
                <div class="tariff__name">Гибкий</div>
                <div class="tariff__price tariff__price-rub">{{resTariff(tariff2)}} <span class="rub rub_25 rub_black">Р</span></div>
                <div class="tariff__description">в месяц</div>
            </div>


        </div>

    </div>
</template>



<script>

    export default {
        props:{

            tariff1: {
                type: Number,
                required: true,
            },
            tariff2: {
                type: Number,
                required: true,
            },
        },
        data () {
            return {
                activeItem: null,
            }
        },
        methods:{
            resTariff(val){
                return val.toString().replace(/\B(?=(\d{3})+(?!\d))/g, " ");
            }
        }

    }
</script>


<style>
    /*tariff__item*/
    .tariff__item{
        display: inline-block;
        width:250px;
        border:1px solid #ccc;
        text-align:left;
        box-shadow: -1px 9px 13px 4px #a09999;
        padding: 10px;
        margin: 5px;

    }
    .tariff__price{
        font-size:30px;
    }
    .tariff__description{
        color:#b1aeae;
        font-size: 12px;
    }
    .tariff__item:hover{
        cursor:pointer;
        opacity:0.7;
    }
    .tariff__item_active{
        background: #e0d7d7;
    }




    /**/
    .rub{

    }
    .rub_25 {
        font-family: arial;
        font-size: 25px !important;
        display: inline-block;
        font-weight: 100;
    }
    .rub_black:before, .rub_black:after, .rub_black {
        border-color: #000 !important;
        color: #000 !important;
    }

    .rub_25:before, .rub_25:after {
        content: "";
        display: block;
        border-bottom: 2px solid #000;
        position: relative;
        left: -1px;
    }


    .rub_25:before {
        width: 8px;
        top: 16px;
    }

    .rub_25:after {
        width: 11px;
        bottom: 11px;
    }


</style>