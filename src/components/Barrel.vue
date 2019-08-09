<template>
<div>
    
    <div class="barrel__image">
        <img class="wobble" src="@/assets/images/barrel--pixel.png">
    </div>
    <div class="barrel__text"><img class="barrel__monkey" src="@/assets/images/barrel--monkey.png">'s in the barrel: <span class="barrel__box">{{ count }}</span></div>
    <button class="button--app" :disabled=" roll == 0 " @click="$emit('update-count')">Add to Barrel</button>
    <!-- <div class="box">
           <strong>{{ count }}</strong>
    </div>  -->

</div>
</template>

<script>
export default{
    props: ['count', 'roll']
}
</script>


<style scoped>
img {
    max-width:250px;
}
.barrel__text {
    display: flex;
    margin: auto;
    justify-content: center;
    align-items: center;
}
.barrel__monkey {
    max-width: 70px;
}
.barrel__box {
    width:36px;
    height:36px;
    line-height: 36px;
    border: 2px solid #eee;
}


</style>