<script>
// import { arrow } from '@popperjs/core';

import SearchBlock from './SearchBlock.vue';
export default {
    components: {

        SearchBlock
    },
    props: [


    ],
    data() {
        return {
            isShow: false,
            chartList: [
                {
                    itemId: "9905538",
                    text: "聖女番茄",
                    number: "2",
                    price: "99",
                    img: "",
                    content: "橘色品種"

                }, {
                    itemId: "9905539",
                    text: "聖女番茄",
                    number: "2",
                    price: "99",
                    img: "",
                    content: "橘色品種"

                }, {
                    itemId: "9905540",
                    text: "聖女番茄",
                    number: "2",
                    price: "99",
                    img: "",
                    content: "橘色品種"

                }
            ],
            isChecked: false,
            tempnum: null,
            refresh: [],
            searchGet: null,
            afterChange: null

        }
    },

    methods: {
        addClick() {
            this.isChecked = !this.isChecked;


            // let existList = JSON.parse(localStorage.getItem("chartList"));
            // let newList = existList !== null ? existList : [];
            // for(let i=0;i<existList.length;i++){
            //     // if(isChecked===true)

            // }
            // setTimeout(() => {
            //     this.isChecked = false;
            // }, 500);

        }
    },
    methods: {
        getIndex(index) { //加法的狀況
            console.log(index)

            let Newarr = [];
            let deletenum =index+1; 
            let arr = JSON.parse(localStorage.getItem("chartList"));
            let num = arr[index].number;
            num = parseInt(num);
            let updateItem = {
                itemId: arr[index].itemId,
                text: arr[index].text,
                number: num + 1,
                price: arr[index].price,
                img: arr[index].img,
                content: arr[index].content
            }
            console.log(updateItem);
            
           
           
            for (let i = 0; i < arr.length; i++) {
                if (i === index ) {
                    
                    Newarr.push(updateItem);
                    
                    
                }
                               
                    Newarr.push(arr[i]);
        
               

            }

            console.log(arr);
            console.log(Newarr);
            Newarr.splice(deletenum, 1);
            this.chartList = Newarr;
            // this.refresh = Newarr;
            return localStorage.setItem("chartList", JSON.stringify(Newarr));
        },
        minusIndex(index) { //減法狀況
            
            console.log(index)
            let deletenum =index+1; 
            let Newarr = []
            let arr = JSON.parse(localStorage.getItem("chartList"));
            let num = arr[index].number;
            let updateItem={};
            num = parseInt(num);
            if(num===0){
                alert('已經歸零，請刪除，或新增數量');
                updateItem = {
                itemId: arr[index].itemId,
                text: arr[index].text,
                number: num,
                price: arr[index].price,
                img: arr[index].img,
                content: arr[index].content
            }
            }else{
                updateItem = {
                itemId: arr[index].itemId,
                text: arr[index].text,
                number: num - 1,
                price: arr[index].price,
                img: arr[index].img,
                content: arr[index].content
            }
            }

            
            
            console.log(updateItem)
           
            for (let i = 0; i < arr.length; i++) {
                if (i === index) {
                   
                    Newarr.push(updateItem);
                

                }
               

                Newarr.push(arr[i]);

            }

            
            console.log(arr);
            console.log(Newarr);
            Newarr.splice(deletenum, 1);
            this.chartList = Newarr;
            return localStorage.setItem("chartList", JSON.stringify(Newarr));
        },
        deleteIndex(index) {

            let arr = JSON.parse(localStorage.getItem("chartList"));
            let Newarr = []
            Newarr = arr.splice(index, 1);
            console.log(arr)
            return localStorage.setItem("chartList", JSON.stringify(arr));
        },
        enforceUpdate(index, number) {


            console.log(index);
            console.log(number);
            let Newarr = []
            let arr = JSON.parse(localStorage.getItem("chartList"));

            let updateItem = {
                itemId: arr[index].itemId,
                text: arr[index].text,
                number: number,
                price: arr[index].price,
                img: arr[index].img,
                content: arr[index].content
            }
            console.log(updateItem)
            arr.splice(index, 1);

            for (let i = 0; i < arr.length; i++) {
                if (i === index) {
                    Newarr.push(updateItem);

                }

                Newarr.push(arr[i]);

            }
            console.log(Newarr);
            this.chartList = Newarr;
            this.refresh = Newarr;
            return localStorage.setItem("chartList", JSON.stringify(Newarr));
        }



    },
    // 生命週期
    mounted() {



        // if (localStorage.getItem("chartList") === null) {
            localStorage.setItem("chartList", JSON.stringify(this.chartList));
        // }///TEST


        this.chartList = JSON.parse(localStorage.getItem("chartList"));



    }
}




</script>
 



<template>
    <div class="info-Area">


        <ol>

            <li v-for="(item, index) in chartList" :key="index" class="item-List">

                <p>商品ID: {{ item.itemId }} </p>
                <p>品名: {{ item.text }} </p>

                <div class="numberBlock">
                    <p>數量:{{ item.number }}</p>
                    <div class="numberDf">
                        <input id="numberInput" class="數量" type="number" v-model="item.number">
                        <!-- {{ item.number }} -->
                        <!-- <p> {{ this.afterChange }}</p> -->

                        <button class="button-function left" @click="enforceUpdate(index, item.number)">update</button>
                    </div>

                </div>


                <div class="price_content">
                    <p>價格: {{ item.price }} </p>
                    <p>{{ item.img }} </p>
                    <p>備註: {{ item.content }} </p>
                </div>
                <!-- <button type="button" @click="getIndex(index)"> {{index}}</button>  -->
                <div class="btn-Area">
                    <button class="button-function" @click="getIndex(index)"><i class="fa-solid fa-plus"> 
                             ADD</i></button>
                    <button class="button-function" @click="minusIndex(index)"><i class="fa-solid fa-minus">
                            MINUS</i></button>
                    <button class="button-function" @click="deleteIndex(index)"><i class="fa-solid fa-x">
                            DELETE</i></button>

                </div>
                <!-- <Btn @addThing="getIndex(index)" /> -->

                <!-- @click="getIndex(index) -->



            </li>


        </ol>


    </div>
</template>

<style lang="scss" scoped>
.info-Area {

    box-sizing: border-box;
}

.item-List {
    padding: 0 30px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 80vw;
    height: 10vw;
    position: relative;
    left: -17px;
    top: 8px;



    background: #b5beb8;
    border: 2px solid #3f4240;
}

.btn-Area {


    box-sizing: content-box;

    flex-direction: column;
    display: flex;
    justify-content: space-around;
    align-items: center;
}

.button-function {

    display: flex;
    justify-content: center;
    text-align: center;
    margin: 2px;

    width: 15vw;
    border: 2px solid #3f4240;
    border-radius: 3px;
    font-size: 14px;
    transition: 1s;
}

.button-function:hover {
    background: #6d7c6f;
    color: #3f4240;
}

.button-function:active {
    scale: 0.8;
}

.numberBlock {
    flex-direction: column;
    display: flex;
    justify-content: center;
    align-items: start;

    .numberDf {
        display: flex;
        justify-content: space-evenly;
    }

    #numberInput {
        width: 8vw;
    }

    .left {

        position: relative;
        left: 37px;
        width: 8vw;

    }
}
.price_content{
    flex-direction: column;
    display: flex;
    justify-content: center;
    align-items: start;
}
</style>