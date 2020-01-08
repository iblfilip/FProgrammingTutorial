<script>
  import { createEventDispatcher } from 'svelte';
  
  const dispatch = createEventDispatcher();

  function goTo(where) {
    dispatch('goTo', {
      path: where
    })
  }
</script>
  <div id="uppernavbardiv">
    <div class="headings">
      <div id="upperheading"> Functional programming</div>
    </div>
  </div>
  <div class="intro">Welcome to  the course of functional programming, start by tutorial and then test your new skills in our quiz. Good luck!</div>
    <div class="inner">
      <button class="act-button" on:click={() => goTo('Tutorial1')}>Start tutorial</button>
      <button class="act-button" on:click={() => goTo('Quiz1')}>Start quiz</button>
    </div>
<style>
 #uppernavbardiv {
    color: white;
    text-align: left;
 }

.headings {
  z-index: 5;
  --webkit-backdrop-filter: blur(4px) saturate(20%);
  left: 20%;
  background-color: rgb(40,40,40);
  height: 7%;
  border-bottom-style: solid;
  border-bottom: thin 1px;
  border-color: black;
  border-bottom-width: 2px;
}

#upperheading{
  margin-left: 1.5%;
  font-size: 33pt;
  font-weight: bold;
}

.intro {
  color: white;
  font-size: 20px;
  padding-top: 50px;
  padding-bottom: 50px;
  padding-left: 30px;
  padding-right: 30px;
}

.inner {
  display: block;
  margin-left: auto;
  margin-right: auto;
  width: 35%;
  padding-top: 100px;
}

.act-button {
  background-color: #dc9135; /* Green */
  border: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  width: 100%;
  margin: 10px;
  font-size: 18px;
}
</style>