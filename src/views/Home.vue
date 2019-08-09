
<template>
    <div>
       <section class="hero is-dark">
           <div class="hero-body">
    <div class="container has-text-centered">
       <h2 class="is-size-2 ">Monkeys in Two Barrels</h2>
      <p>Voted "The game of the century" and "Masterful, an elegant game of skill" </p>
    </div>
  </div>
       </section>
    
       <div class="container has-padding-vertical">
            <div class="columns">
          <div class="column">
         <Rules></Rules>
            <div class="box box--dashed">
                  <p>You have <strong>{{  turnsRemaining }}</strong> rolls remaining.</p>
            </div>
              <!-- <Dice :rolled="roll"></Dice> -->
            <p v-if=" roll == 0 ">Roll the die!</p>
            <p v-else>You Rolled: <strong>{{ roll }}</strong> </p>
            <button class="button--app " @click="rollDie" :disabled="roll > 0">Roll</button>
                 
          </div>
            <div class="column has-text-centered">
                <Barrel 
                :count="barrelOne" 
                v-on:update-count="addToBarrelOne"
                :roll="roll"></Barrel>
            </div>
            <div class="column has-text-centered">       
                <Barrel 
                :count="barrelTwo"
                v-on:update-count="addToBarrelTwo"
                :roll="roll"></Barrel>
            </div>
        </div>
       </div>
    </div>
</template>



<script>
import Barrel from '@/components/Barrel.vue';
import Dice from '@/components/Dice.vue';
import Rules from '@/components/Rules.vue';
    export default {
         components: {
            Barrel,
            Dice,
            Rules
        },
        data: function(){
            return{
                barrelOne: 0,
                barrelTwo: 0,
                roll: 0,
                hasRolled: false,
                turnsRemaining: 6
            }
        },
        methods: {
          resetGame(){
                this.barrelOne= 0;
                this.barrelTwo= 0;
                this.roll= 0;
                this.hasRolled= false;
                this.turnsRemaining= 6;
          },
          rollDie(){
                this.turnsRemaining --;
                this.roll= Math.floor(Math.random() * ((6 - 1) + 1) + 1);
                return;
          },
          addToBarrelOne(){
            this.barrelOne += this.roll;
            this.checkRemainingRolls();
          },
          addToBarrelTwo(){
            this.barrelTwo += this.roll;
            this.checkRemainingRolls();
          },
          compareBarrels(){
              if( this.barrelOne == this.barrelTwo){
                  alert('Hoorah! You did it! Play Again?');
                  this.resetGame();
                  return;
              }
              else {
                  alert('Sorry, try again?');
                  console.log(this.barrelOne + ' ' + this.barrelTwo);
                  this.resetGame();
                  return;
              }
          },
          checkRemainingRolls(){
               if(this.turnsRemaining > 0){
                 this.roll = 0;
                 return;
               }
               else{
                   this.compareBarrels();
               }
          }

        }

    }
</script>
<style>

</style>