<script>
  import { createEventDispatcher } from 'svelte';
  import { onMount } from 'svelte';

  const dispatch = createEventDispatcher();

  export let score

  function goTo(path) {
    dispatch('goTo', {
      path
    })
  }

</script>
<div id="uppernavbardiv">
    <div class="headings">
      <div id="upperheading">Quiz</div>
    </div>
  </div>
{#if score > 8}
<div class="congratulation">Congratulations!</div>
{:else}
<div class="congratulation">You looser!</div>
{/if}
<div class="intro">Your score is {score}/12.5</div>
<div class="centered">
  <button on:click={() => goTo('Welcome')} class="act-button">Return to main menu</button>
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

.congratulation {
  color: white;
  font-size: 20px;
  padding-top: 50px;
}

.intro {
  color: white;
  font-size: 20px;
  padding-top: 50px;
  padding-bottom: 50px;
}

.centered {
  margin-left: auto;
  margin-right: auto;
  width: 30%;
}

.act-button {
  background-color: #dc9135; /* Green */
  border: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  margin: 10px;
  font-size: 16px;
}

</style>