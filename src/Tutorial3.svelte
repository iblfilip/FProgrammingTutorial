<div id="uppernavbardiv">
  <div class="headings">
    <div id="upperheading">Loops</div>
  </div>
</div>
<div class="content">
  <h2>For loops</h2>
  <p>We can define a reference on a list:</p>
  <code>let test = ref []</code>
  <hr>
  <p>OCaml has a simple for loop to iterate on integers in a range:</p>
  <code>for i = 1 to 20 do test := i :: !test;done;!test</code>
  <hr>
  <p>Here, for every value between 1 and 20, we have added it in this order at the head of the reference.</p>
  <p>If we would like them in the correct order, we have to reverse the list:</p>
  <code>List.rev !test</code>
  <hr>
  <p>Or we can execute the loop directly from the upper bound to the lower bound:</p>
  <code>for i = 10 downto 1 do test := i :: !testdone;!test</code>
  <hr>
  <h2>While loops</h2>
  <p>Additionally, OCaml provides a while loop to execute code while an expression is true:</p>
  <code>while !x > 20 do</code>
  <code>print_int !x; print_newline ();</code>
  <code>x := !x - 2</code>
  <hr>

  <div class="inner">
    <button class="act-button" on:click={() => goTo('Tutorial2')}>Back</button>
    <button class="act-button" on:click={() => goTo('Tutorial4')}>Next</button>
  </div>
</div>

<script>
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  function goTo(where) {
    dispatch("goTo", {
      path: where
    });
  }
</script>

<style>
  h2 {
    color: #d8bf9f;
    font-size: 18px;
    padding-top: 15px;
    padding-bottom: 5px;
    text-align: left;
    padding-left: 5px;
  }

  p {
    color: white;
    text-align: left;
    padding-top: 5px;
  }

  code {
    text-align: left;
    padding-left: 5px;
    margin-bottom: 20px;
  }

  #uppernavbardiv {
    color: white;
    text-align: left;
  }

  .headings {
    z-index: 5;
    --webkit-backdrop-filter: blur(4px) saturate(20%);
    left: 20%;
    background-color: rgb(40, 40, 40);
    height: 7%;
    border-bottom-style: solid;
    border-bottom: thin 1px;
    border-color: black;
    border-bottom-width: 2px;
  }

  #upperheading {
    margin-left: 1.5%;
    font-size: 33pt;
    font-weight: bold;
  }

  .content {
    overflow: auto;
    padding: 10px 20px 10px 20px;
    bottom: 100px;
    height: 575px;
  }

  .actions {
    position: absolute;
    left: 10%;
    right: 10%;
    bottom: 5%;
  }
  .inner {
    display: flex;
    justify-content: space-between;
    margin-left: auto;
    margin-right: auto;
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
