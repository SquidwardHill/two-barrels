<template>
  <div>
    <p class=" has-text-centered"><em class="color--creamsicle text--small">And you may ask yourself, well how did I get here?</em></p>
    <section class="hero font--primary has-text-centered">
      <div class="hero-body">
        <div class="container ">
          <h1 class="is-size-2 color--light">
          Why I made this 👇
          </h1>
        </div>
      </div>
    </section>
    <section>
      <div class="columns is-centered">
        <div class="column  is-8">
          <div class="container has-padding">
             <div class="has-borders--vertical">
            <p class="is-size-5"> <strong>Well, I made Monkeys in Two Barrels for a couple of reasons.</strong></p>
            <br>
            </div>  
              <ol>
                <li>Primarily, I would like to be considered for the <a href="https://www.twobarrels.com/jobs/software/developer/">Junior Software Engineer</a> position at Two Barrels. </li>
                <li>I'm teaching myself Vue.js, so this has been a more practical application of my learnings thus far. Because the game is my own brain child, I didn't just follow along with a tutorial like a zombie.</li>
              </ol>
            <div class="process">
                <p><strong>Process | Code Step through</strong></p>
              <br>
              <div class="columns">
                <div class="column process-images">
                 <img src="@/assets/images/process-screenshot.png">
                </div>
                <div class="column">
                  <img src="@/assets/images/design-screenshot.png">
                </div>
              </div>
            </div>
          <!-- end image columns -->
          <br>
          <ul>
            <li>I came across a job posting by Two Barrels on Indeed and popped over to the website to learn more. After reading through the "How to get a job" section, I came up with the idea to make a little game in Vue.js for my application. </li>
           
            <li>I set up the initital project with Vue CLI, and then wrote out a rough draft of the game logic, and the structure of the application. I then created the routes, views, and components I decided to use.  </li>
           
            <li>The majority of the game logic is controlled in the Home view component. The initial state of the game is held in an object returned by the data function of the home component. </li>

            <li>In order to start the game, the user clicks the "roll die" button. The button uses the <span class="code">v-on</span> directive, which accepts <span class="code">RollDie()</span> method. Within this method, the value of the <span class="code">roll</span> property is updated, and the <span class="code">turnsRemaining</span> property is decremented. </li>
           
           <li>
              In order to communicate to the parent Barrel component that the child's "add to barrel" button has been clicked and to therefore update the total, I used the <span class="code">$emit</span> method to pass up the name of the event.
           </li>

           <li>The parent barrel component then listens for the event emitted and triggers the appropriate update methods, followed by a series of checks to compare values and determine whether the game should continue running.</li>

           <li>If there are turns remaining, the game continues to run. If there are no turns remaining, the barrel totals are compared to determine a win or a loss- which triggers the Modal component. The outcome is passed as a prop to the child modal component, and the close button triggers the <span class="code">$emit</span> method - which the parent listens for and calls the <span class="code">ResetGame()</span>  method.</li>

           <li>Fin. 👏</li>
          </ul>
         
          </div>
       
        

        
        </div>
        </div>
     
    </section>
  </div>
</template>

<style lang="scss" scoped>
.hero {
    background-image: url('~@/assets/images/monkey-banner.jpg');
    background-repeat: no-repeat;
    background-size: cover;
    transition:.5s ease;
    &:hover {
      background-image: url('~@/assets/images/talking-heads-banner.jpg');
      background-repeat: no-repeat;
      background-size: cover;
      transition:.5s ease;
    }
    // background-position: 50% 50%;
}

.has-borders--vertical {
  position:relative;
   margin-bottom:1rem;
  &:before {
    content: "";
    background: map-get($map: $colors, $key: primary);
    bottom: 0;
    position: absolute;
    width: 100px;
    height: 4px;
   
  }
}
ul li {
  margin-bottom: 1rem;
}
 ol {
  list-style: none;
  counter-reset: my-awesome-counter;
  margin-bottom: 4rem;
}
ol li {
  counter-increment: my-awesome-counter;
  margin-bottom:1rem;
}
ol li::before {
  content: counter(my-awesome-counter) ". ";
  color: map-get($map: $colors, $key: primary);
  font-weight: bold;
  //border:1px solid #eee;
  font-size:1.5rem;
  left: -1em;
}
.process {
  border-top: 1px solid #eee;
  padding-top: 2rem;
}

</style>
