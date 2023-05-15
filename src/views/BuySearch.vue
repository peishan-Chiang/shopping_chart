<script>



export default {
    components: {
     
        
    },
    props: [
        
    ],
    data() {
        return {
           
        }
    },
    methods: {
       
    },
    // 生命週期
    mounted() {
        // this.fn();
    }
}




</script>
 



<template>
    <div class="bg">
        <div class="heading">
            <div class="searching ">
              
            </div>
        
        </div>
        
        <div class="bodyBlock">
           
            <ListArea />

            

            <div class="info">
                
            </div>

        </div>


            
    </div>
    
</template>

<style lang="scss" scoped>
.bg {

    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    background: #afada2;
    opacity: 1; //透明度 0 (不顯示)~1(不透明)
    z-index: -1;
}

.heading {
    flex-direction: column;
    display: flex;
    justify-content: center;
    align-items: center;
    position: absolute;
    left: 120px;
    top: 20px;
    width: 80%;
    height: 2vw;
    background: #faf6f6;
    border: 2px solid #9e978b;

}
.info{
    z-index: 1;
}
</style>