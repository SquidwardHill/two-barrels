<template>
<footer>
<div class="columns is-centered">
    <div class="column is-8 has-text-centered">
     <div class="potfolio__icons">
        <a href="https://github.com/SquidwardHill" target="_blank" alt="Github"><img src="@/assets/images/icon--github.svg"></a>
        <a href="https://www.linkedin.com/in/sydneyehill/" target="_blank" alt="Linkedin"><img src="@/assets/images/icon--linkedin.svg"></a>
        <a href="mailto:sydneyehill@gmail.com" target="_blank" alt="Email"><img src="@/assets/images/icon--email.svg"></a>
        <a href="https://sydneyhill.io" target="_blank" alt="Portfolio"><img src="@/assets/images/icon--astronaut.svg"></a>
     </div>
    </div>
</div>
</footer>
</template>

<style lang="scss" scoped>
footer{
     background-color: map-get($colors, secondary); 
     color:  map-get($colors, light-grey); 
}
img {
    max-width:24px;
    margin:1rem .5rem 0 .5rem;
    opacity: 0.5;
}
</style>
