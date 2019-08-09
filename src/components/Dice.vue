<template>
<div>
<p v-if=" rolled == 0 ">Roll the die!</p>
<p v-else>You Rolled: {{ rolled }} </p>
<button class="button--app " @click="rollDie" :disabled="rolled > 0">Roll</button>
</div>
</template>

<script>

export default {
    props: ['rolled'],
}
</script>