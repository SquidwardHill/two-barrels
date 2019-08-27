
<template>
    <div>
       <section>
           
            <div class="columns">
                <div class="column is-one-third background-color--light-grey font--primary game-rules">
                    <div class="has-padding">
                         <h2 class="is-size-2 is-strong ">Monkeys in Two Barrels</h2>
                        <p><em class="highlight">Critics called it "The game of the century!" and "Masterful, an elegant game of skill." </em></p>
                        <hr class="background-color--creamsicle">
                        <Rules></Rules>
                    </div>
                 </div>
                <div class="column background-color--primary is-two-thirds font--game">
                   <div class="has-padding">
                        <div class="roll is-flex-desktop color--light">
                            <div class="roll--count">
                                    <span>You have <strong>{{  turnsRemaining }}</strong> rolls remaining.</span>
                            </div>

                           <div class="roll--dice is-flex">
                                <span v-if=" roll == 0 ">Roll the die!</span>
                                <span v-else>You Rolled: <span class="text--large"> {{ roll }} </span> </span>
                                <button class="app-button button--white " @click="rollDie" :disabled="roll > 0">Roll</button>
                           </div>

                            
                        </div>
                    <Barrel 
                    :count="barrelOne" 
                    v-on:update-count="addToBarrelOne"
                    :roll="roll"
                    :wobble="wobbleOne"
                    ></Barrel>
        

                    <Barrel 
                    :count="barrelTwo"
                    v-on:update-count="addToBarrelTwo"
                    :roll="roll"
                    :wobble="wobbleTwo"
                    ></Barrel>
                   </div>
                </div>   
            </div>
       </section>
       <Modal
        v-show="isModalVisible"
        @close="closeModal"
        :outcome="outcome">
        </Modal>
    </div>
</template>



<script>
import Barrel from '@/components/Barrel.vue';
import Rules from '@/components/Rules.vue';
import Modal from '@/components/Modal.vue';
    export default {
         components: {
            Barrel,
            Rules,
            Modal
        },
        data: function(){
            return {
                barrelOne: 0,
                barrelTwo: 0,
                roll: 0,
                hasRolled: false,
                turnsRemaining: 6,
                isModalVisible: false,
                outcome: " ",
                wobbleOne: " ",
                wobbleTwo: " " 
            }
        },
        methods: {
          resetGame(){
                this.barrelOne= 0;
                this.barrelTwo= 0;
                this.roll= 0;
                this.hasRolled= false;
                this.turnsRemaining= 6;
                this.closeModal();
          },
          rollDie(){
                this.wobbleOne = " ";
                this.wobbleTwo = " ";
                this.turnsRemaining --;
                this.roll= Math.floor(Math.random() * ((6 - 1) + 1) + 1);
                return;
          },
          addToBarrelOne(){
            this.wobbleOne = "wobble";
            this.barrelOne += this.roll;
            this.checkRemainingRolls();
          },
          addToBarrelTwo(){
            this.wobbleTwo = "wobble";
            this.barrelTwo += this.roll;
            this.checkRemainingRolls();
          },
          compareBarrels(){
              if( this.barrelOne == this.barrelTwo){
                  this.outcome = "You Win!"
                  this.showModal();
                  return;
              }
              else {
                  this.outcome = "You Lose!"
                  this.showModal();
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
          },
          showModal() {
                this.isModalVisible = true;
            },
            closeModal() {
                 this.isModalVisible = false;
                  this.resetGame();
            }
        }

    }
</script>

<style lang="scss" scoped>
.game-rules {
    background-image: url('~@/assets/images/barrel--monkey-bg.png');
    background-repeat: no-repeat;
    background-position: 0% 100%;
}
.highlight {
    color: #969696;
    background-color: white;
}
.roll {
    border: 1px solid white;
    padding: 2rem;
    margin: 0 0 2rem 0;
    align-items: center;
    &--dice {
    align-items: center;
    }
}

 @media(min-width:980px){
    .roll--count {
        margin-right: 5rem;
    }
}
</style>
