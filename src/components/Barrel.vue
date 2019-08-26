<template>
    <div class="barrel">
        <div class="barrel__image">
            <img :class="wobble" src="@/assets/images/barrel--pixel.png">
        </div>
    <div class="barrel__content">
            <div class="barrel__text color--creamsicle">Monkeys in the barrel: <span class="barrel__box">{{ count }}</span></div>
            <button class="app-button button--light" :disabled=" roll == 0 " @click="$emit('update-count'); toggleWobble();">Add to Barrel</button>
    </div>
    </div>
</template>

<script>
export default{
    data: function(){
        return{
            isWobble: false
        }
    },
    props: ['count', 'roll', 'wobble'],
    methods: {
        resetWobble(){
            this.isWobble = false;
        },
        toggleWobble(){
            this.isWobble = true;
        }
    }
}
</script>


<style scoped>
img {
    max-width:250px;
}
/* .barrel__text {
    display: flex;
    margin: auto;
    justify-content: center;
    align-items: center;
} */
.barrel {
    display:flex;
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
    padding: 2px 8px;
    color: #363636;
}


</style>