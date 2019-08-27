<template>
  <transition name="modal-fade">
  <div class="app-modal--backdrop font--game">
    <div class="app-modal">
       <button
            type="button"
            class="button--close"
            @click="close"
          >
            x
          </button>
      <section class="app-modal--body has-text-centered">
          <p>{{ outcome }}</p>
          <div> <img class="hop" src="@/assets/images/barrel--monkey.png"></div>

         <button
              type="button"
              class="app-button button--secondary"
              @click="close"
            >
              Play Again?
          </button>
       </section>
       
    </div>
  </div>
  </transition>
</template>

<script>
  export default {
    props:['outcome'],
    methods: {
      close() {
        this.$emit('close');
      },
    },
  };
</script>

<style lang="scss" >
.modal-fade-enter,
  .modal-fade-leave-active {
    opacity: 0;
  }

  .modal-fade-enter-active,
  .modal-fade-leave-active {
    transition: opacity .5s ease
  }

  .app-modal {
    padding: 2rem;
    position: relative;
    background: #FFFFFF;
    box-shadow: 2px 2px 20px 1px;
    overflow-x: auto;
    display: flex;
    flex-direction: column;
    p {
        padding-bottom: 1rem;
    }
    &--backdrop {
        position: fixed;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        background-color: rgba(0, 0, 0, 0.3);
        display: flex;
        justify-content: center;
        align-items: center;
    }
    &--body {
        padding: 1rem;
    }
  }

  .button--close {
    border: none;
    font-size: 20px;
    cursor: pointer;
    font-weight: bold;
    color: #4AAE9B;
    background: transparent;
    position: absolute;
    top: .5rem;
    right: .5rem;
  }

</style>