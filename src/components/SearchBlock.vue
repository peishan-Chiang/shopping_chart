<script>

export default {
    components: {


    },
    props: [

    ],
    data() {
        return {


            searchItem : " ",
            chartList : " "


            // text: "聖女番茄",
            // number: "2",
            // price: "99",
            // img: "",
            // content: "橘色品種"

        }
    },

    methods: {
        submitID() {
            console.log('push')
            this.$emit("emitPush", this.itemId) //傳回BuyChart要做ListArea做匯總


        },
        backPage() {
            this.$router.push("/");
        }



    },
    // 生命週期
    mounted() {
        this.chartList = JSON.parse(localStorage.getItem("chartList"));
    }
}




</script>
 



<template>
    

    <div class="heading-Area">
        <nav class="navbar navbar-light bg-light rounded-1 ">
            <div class="container-fluid">
                <form class="d-flex">
                    <!-- <input class="form-control me-5 fs-6 mx-5" type="text"
                     placeholder="指定商品ID" aria-label="Search" v-model="itemId">
                    <button class="btn btn-outline-success fs-6 w-75 mx-1 " type="button"
                    v-on:click="submitID" >
                 
                        <i class="fa-solid fa-list">編號指定加入 </i></button> -->



                    <!-- <input class="form-control me-5  fs-6 mx-5" type="text" placeholder="關鍵字搜尋" aria-label="Search"
                        >
                    <button class="btn btn-outline-success fs-6  w-50" type="button" >
                        <i class="fa-solid fa-magnifying-glass ">搜尋</i></button> -->

                </form>

            </div>
        </nav>
        <!-- 結帳 -->
        <nav class="navbar navbar-light bg-light rounded-1 d-flex fs-6">
            <form class="container-fluid justify-content-start d-flex fs-6">
                <button class="btn btn-outline-success me-5 fs-6 mx-4" type="button" @click="backPage">
                    <i class="fa-solid fa-house">返回主頁</i>
                </button>

                <button class="btn btn-outline-success me-5  mx-5 " type="button">
                    <i class="fa-solid fa-backward">返回搜尋頁面</i>
                </button>

                <button class="btn btn-outline-success me-5 " type="button">
                    <i class="fa-solid fa-cart-shopping">前往結帳</i>
                </button>

            </form>
        </nav>



    </div>
</template>

<style lang="scss" scoped>
.heading-Area {
    width: 95vw;
    border-radius: 5px;
    background: #faf6f6;
    display: flex;
    justify-content: center;
    align-items: center;
}

.mark {
    background: orange;
    color: black;
}
</style>