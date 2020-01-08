<div id="uppernavbardiv">
  <div class="headings">
    <div id="upperheading">Anonymous functions</div>
  </div>
</div>
<div class="content">
  <h2>Anonymous functions</h2>
  <p>OCaml supports anonymous functions, which are functions defined without being bound to an identifier. For instance:</p>
  <code>(fun x -> x + 1) 22</code>
  <hr>
  <p>We can bound an anonymous function to an identifier. Hence, we will have multiple ways to define functions:</p>
  <code>let incr = fun x -> x + 1</code>
  <code>incr 22</code>
  <h2>Iterators</h2>
  <p>We can mix anonymous functions and iterators. Let's try an example with a list. If we would like to increment all elements of a list, we can use List.map:</p>
  <code>List.map (fun x -> x + 1) [ 1; 2; 3; 4 ]</code>
  <hr>
  <p>Here, x is an element of the list, x + 1 is the operation that will be done on x. The result will be a list with all elements incremented by 1.</p>
  <p>Next, we can see an example with fold_left. If we would like to compute the sum of all elements of a list, we can do this:</p>
  <code>List.fold_left (fun acc x -> acc + x) 0 [ 1; 2; 3; 4 ]</code>
  <hr>
  <p>If we have :</p>
  <code>let plus = fun acc x -> acc + x</code>
  <hr>
  <p>then:</p>
  <code>List.fold_left plus 0 [ 1; 2; 3; 4 ]</code>
  <hr>
  <p>is equivalent to:</p>
  <code>plus (plus (plus (plus 0 1) 2) 3) 4</code>
  <hr>
  <p>To finish, we can print the values of a list as follows:</p>
  <code>List.iter print_int [ 1; 2; 3; 4 ]</code>
  <hr>

  <div class="inner">
    <button class="act-button" on:click={() => goTo('Tutorial3')}>Back</button>
    <button class="act-button" on:click={() => goTo('Tutorial5')}>Next</button>
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
