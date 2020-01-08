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
  <div class="intro" style="font-weight: bold;font-family: Helvetica">Welcome to our course of functional programming, start by reading the tutorial and if you have the courage, try your luck in our quiz.</div>
  <div class="ext" style="font-weight: bold;font-family: Helvetica">You should bear in mind that, we have selected OCaml as the language of this application, without any particular reason. </div>
    <div class="ext" style="font-weight: bold;font-family: Helvetica">The quiz consists of 6 questions, 2.0 points for a correct answer, -0.5 for incorrect one. </div>
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

.ext {
  color: white;
  font-size: 20px;
  padding-top: 10px;
  padding-bottom: 30px;
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