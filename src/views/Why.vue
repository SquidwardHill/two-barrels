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
        <div class="column is-8">
          <div class="container has-padding">
             <strong> <p class="is-size-5 emphasize--primary">Well, I made Monkeys in Two Barrels for a couple of reasons.</p></strong>
            <br>
              <ol>
                <li>Primarily, I would like to be considered for the <a href="https://www.twobarrels.com/jobs/software/developer/" target="_blank">Junior Software Engineer</a> position at Two Barrels. </li>
                <li>I'm teaching myself Vue.js, so this has been a more practical application of my learnings thus far. Because the game is my own brain child, I didn't just follow along with a tutorial like a zombie.</li>
              </ol>
                <hr class="primary">
            <div class="process">
               <p class="is-size-5 emphasize--primary"> <strong>How I made this.</strong></p>
            
               <br>
              <!-- <p>I came across a job posting by Two Barrels on Indeed and popped over to the website to learn more. After reading through the "How to get a job" section, I pondered my approach. Over a very enlightening dog walk, the idea to make this little game in Vue.js came to me. </p><br> -->
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
           <p><strong>Process | Code Step through</strong></p>
            
          <ul>
            <!-- <li><strong><em>Overview</em></strong></li> -->

            <li>After deciding on how the game should work, I wrote out a rough draft of the game logic, and considered the structure of the application. I used the Vue CLI for project scaffolding-- then set up the routes, views, and components I decided on.  </li>
           
            <li>The majority of the game data and logic is set up in the Home view component. Here, all of the game's reactive data properties are initialized in the component's data object.</li>

            <li>In order to start the game, the user clicks the "roll die" button. The button uses the <span class="code">v-on</span> directive, which accepts <span class="code">RollDie()</span> method. Within this method, the value of the <span class="code">roll</span> property is updated, and the <span class="code">turnsRemaining</span> property is decremented. </li>
           
           <li>
              In order to communicate to the parent Barrel component that the child's "add to barrel" button has been clicked and to therefore update the total, I used Vue's built in <span class="code">$emit</span> method to pass up the name of the event.
           </li>

           <li>The parent Barrel component listens for the event emitted, which triggers the appropriate update methods, followed by a series of checks to compare values and determine whether the game should continue running.</li>

           <li>If <span class="code">turnsRemaining > 0</span>, the roll is reset and the game continues to run. Else, the barrel totals are compared to determine a win or a loss and the Modal component is triggered. </li>

           <li>The outcome is passed as a prop to the child Modal component, and the close button triggers the <span class="code">$emit</span> method - which the parent listens for and calls the <span class="code">ResetGame()</span>  method.</li>

           <li>Fin. 👏</li>
          </ul>
         <hr class="primary">
         
      
          <p><strong>Blockers | Future</strong></p>

          <p>The thing I found most challenging during this project was state management and determing the pattern I wanted to work with. Because its a fairly small and simple game- I went with the most straight forward option (to me) that I could complete most efficiently.</p>

          <p>Improvements I would like to make include refactoring the project to include an event bus, and potentially breaking it down into even smaller, building block components. Based on the specific job description, I should probably make this in Ruby next.</p>
       
           <p>Feel free to see the project <a href="https://github.com/SquidwardHill/two-barrels" target="_blank"><em>here</em></a>.</p>
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


</style>
