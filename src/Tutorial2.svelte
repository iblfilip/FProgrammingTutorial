<div id="uppernavbardiv">
  <div class="headings">
    <div id="upperheading">Conditionals</div>
  </div>
</div>
<div class="content">
  <h2>Booleans</h2>
  <p>Booleans in OCaml can be either true or false. They are often created when comparing other values. For instance:</p>
  <code>5 > 2</code>
  <hr>
  <p>OCaml's comparison operators can be used on values of any type, not only on numerical values. We can compare strings and characters as well:</p>
  <code>"dddddddd" &lt; "bbb"</code>
  <code>"14" &lt;= "224"</code>
  <code>33 >= 22</code>
  <hr>
  <p>To test for equality, we can use = and for inequality we can use &lt;>. For instance:</p>
  <code>10 = 10</code>
  <code>5 &lt;> 5</code>
  <code>"15" = 15</code>
  <hr>
  <p>OCaml does not allow to compare values of different types.</p>
  <h2>If-else</h2>
  <p>Let’s define two values:</p>
  <code>let a = 1 and b = 2</code>
  <hr>
  <p>We can compute the minimum of them:</p>
  <code>printf.printf "min(%d,%d) = %d\n" a b (if a &lt; b then a else b)</code>
  <hr>
  <p>We can of run sequences within branches:</p>
  <code>let z = if a &lt; 5500 then begin print_string "return at least 5500 !"; print_newline (); 5500 end else a</code>
  <hr>

  <div class="inner">
    <button class="act-button" on:click={() => goTo('Tutorial1')}>Back</button>
    <button class="act-button" on:click={() => goTo('Tutorial3')}>Next</button>
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
