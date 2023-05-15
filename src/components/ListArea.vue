<script>
import ItemBar from '../components/IteamBar.vue';

export default {
    components: {

        ItemBar

    },
    props: [

    ],
    data() {
        return {


        }
    },
    methods: {
        fn() {






        }
    },
    // 生命週期
    mounted() {
        
    }
}




</script>
 



<template>
    <div class="body-Area">
        <div class="List-Area">
           

            <ItemBar />




        </div>
    </div>


    <div class="bodyBlock">
        <div class="info"></div>
    </div>
</template>

<style lang="scss" scoped>

.body-Area{

    flex-direction: column;
    display: flex;
    justify-content: center;
    align-items: center;
    width: 95%;
    height: 30vw;
    position: relative;
    top:15vh;
    left: 2vw;
    background:hsl(135, 4%, 40%);
    border-radius: 5px;
}
.List-Area{
    height: 80%;
    border:3px #4f5e56;
    border-radius: 5px ;
    background:hsl(135, 4%, 82%);
    overflow-y: auto;
}
</style>