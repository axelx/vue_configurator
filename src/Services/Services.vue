<template>
    <div>
        <div class="services">
            <div class="serveces__title">Сервисы и лицензии</div>
            <div class="serveces__checkbox"></div>

            <div v-for="(license,index) in licenses">
                <input
                        type='checkbox'
                        class="ios8-switch ios8-switch-sm "
                        v-bind:id="'checkbox-' + index"
                        v-model="checkedLicense"
                        v-bind:value="license.price"
                >
                <label  v-bind:for="'checkbox-' + index">{{license.name}}</label>
            </div>

            <span>{{selectedLicense()}}</span>
        </div>

    </div>
</template>



<script>

    export default {
        data () {
            return {

                licenses: [
                    {
                        id: 1,
                        name: 'Microsoft Windows',
                        price: 1300,
                    },
//                    {
//                        id: 2,
//                        name: 'Linux',
//                        price: 150,
//
//                    },
//                    {
//                        id: 3,
//                        name: 'Ubuntu',
//                        price: 50,
//
//                    },
//                    {
//                        id: 4,
//                        name: 'Mint',
//                        price: 250,
//
//                    },
                ],
                checkedLicense: []
            }
        },
        methods:{
            selectedLicense(){

                let sum=0;
                for(let i=0;i<this.checkedLicense.length;i++){
                    sum = sum + parseInt(this.checkedLicense[i]);
                }
                this.$emit('selectedLicense',sum)
            }
        }

    }
    
    
</script>


<style>
    /*services*/
    .services{
        background: #eee;
        margin: 20px;
        padding: 15px;
        border-radius: 10px;
    }
    .serveces__title{
        font-size:18px;
        margin-bottom:10px;
        /*padding:10px;*/
    }



    /* КНОПКА КАК в АЙФОНЕ*/

    input[type="checkbox"].ios8-switch {
        position: absolute;
        margin: 8px 0 0 16px;
        display: none;
    }
    input[type="checkbox"].ios8-switch + label {
        position:relative;
        padding: 5px 0 0 50px;
        line-height: 2.0em;
    }
    input[type="checkbox"].ios8-switch + label:before {
        content: "";
        position: absolute;
        display: block;
        left: -1px;
        top: 0;
        width: 40px; /* x*5 */
        height: 24px; /* x*3 */
        border-radius: 16px; /* x*2 */
        background: #fff;
        border: 1px solid #d9d9d9;
        -webkit-transition: all 0.3s;
        transition: all 0.3s;
    }
    input[type="checkbox"].ios8-switch + label:after {
        content: "";
        position: absolute;
        display: block;
        left: 0px;
        top: 2px;
        width: 24px; /* x*3 */
        height: 24px; /* x*3 */
        border-radius: 16px; /* x*2 */
        background: #fff;
        border: 1px solid #d9d9d9;
        -webkit-transition: all 0.3s;
        transition: all 0.3s;
    }
    input[type="checkbox"].ios8-switch + label:hover:after {
        box-shadow: 0 0 5px rgba(0,0,0,0.3);
    }
    input[type="checkbox"].ios8-switch:checked + label:after {
        margin-left: 16px;
    }
    input[type="checkbox"].ios8-switch:checked + label:before {
        background: #B44536;
    }

    /* SMALL */

    input[type="checkbox"].ios8-switch-sm {
        margin: 5px 0 0 10px;
    }
    input[type="checkbox"].ios8-switch-sm + label {
        position: relative;
        padding: 0 0 0 32px;
        line-height: 1.3em;
    }
    input[type="checkbox"].ios8-switch-sm + label:before {
        width: 25px; /* x*5 */
        height: 17px; /* x*3 */
        border-radius: 10px; /* x*2 */
    }
    input[type="checkbox"].ios8-switch-sm + label:after {
        width: 13px; /* x*3 */
        height: 13px; /* x*3 */
        border-radius: 10px; /* x*2 */
    }
    input[type="checkbox"].ios8-switch-sm + label:hover:after {
        box-shadow: 0 0 3px rgba(0,0,0,0.3);
    }
    input[type="checkbox"].ios8-switch-sm:checked + label:after {
        margin-left: 10px; /* x*2 */
    }



</style>