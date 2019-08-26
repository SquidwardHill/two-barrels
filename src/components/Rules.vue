<template>
    <section class="has-text-left">
        <div class="rule">
            <h4 class="is-size-4 is-strong">The Goal:</h4>   
            <p>Try to get an equal amount of monkeys in both barrels (think BlackJack)</p>
        </div>
        <div class="rule">
            <h4 class="is-size-4 is-strong">How to Play:</h4> 
            <ul class="list--bulleted">
                <li class="list__item">Roll the die to determine the number of monkeys</li>
                <li class="list__item">Put the number of monkeys you rolled into <strong>one</strong> of the barrels</li>
                <li class="list__item">Repeat until your turns are up</li>
            </ul>
        </div>
    <!-- <p>This game requires great skill, and was artfully crafted my a master game architect. Good luck.</p> -->
    </section>
</template>

<style lang="scss"  scoped>
.list {
    &--bulleted {
        list-style: disc;
    }
    &__item {
        margin-left: 1rem;
    }
}
.rule {
    margin-bottom: 3rem;
}
</style>