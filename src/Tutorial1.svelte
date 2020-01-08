<div id="uppernavbardiv">
  <div class="headings">
    <div id="upperheading">Introduction</div>
  </div>
</div>
<div class="content">
  <h2>Variables</h2>
  <p>We can associate a name to a value. To do this, the let keyword is used which associates the result of some computation with a name:</p>
  <code>let x = 5 * 4</code>
  <hr>
  <p>We can use the name where we would like the value:</p>
  <code>let y = x + 2</code>
  <h2>Mutable Variables</h2>
  <p>We cannot change the value associated with a variable after its definition. Trying to do so would trigger a compilation error:</p>
  <code>x &lt;- x + 1</code>
  <hr>
  <p>To modify the value of a variable, a trick must be used. The ref function creates a special value (a reference) that can be modified later:</p>
  <code>let x = ref 42</code>
  <hr>
  <p>Then, we can change the value of the reference associated with x using the := operator:</p>
  <code>x := 100 / 2</code>
  <hr>
  <p>We can also access the value contained in the reference using the ! operator:</p>
  <code>let y = !x + 1</code>
  <h2>List and arrays</h2>
  <p>Lists and arrays are predefined data structures, for instance we can have a list of integers:</p>
  <code>[ 1; 50; 33 ]</code>
  <p>An array of strings:</p>
  <code>[|"John"; "Watson"|]</code>
  <h2>List operations</h2>
  <p>Predefined functions can be used on lists, for example reversing the list:</p>
  <code>List.rev [3; 2; 1]</code>
  <hr>
  <p>Get the head of the list:</p>
  <code>List.hd [3; 2; 1]</code>
  <hr>
  <h2>Array operations</h2>
  <p>We can use predefined functions on arrays, for instance concatenating two arrays:</p>
  <code>Array.append [| 1; 2 |] [| 3; 4; 5 |]</code>
  <hr>
  <p>To get the element number i of an array, wehave two ways to do this ( the first element has number 0):</p>
  <code>Array.get [| 42; 51; 32 |] 2</code>
  <p>or</p>
  <code>[| 42; 51; 32 |].(2)</code>
  <hr>
  <h2>Basic string operations</h2>
  <p>A string is a sequence of characters. We can create a string from just one character:</p>
  <code>String.make 5 'x'</code>
  <hr>
  <p>Strings can also be made by joining other strings:</p>
  <code>"Kate" ^ " and " ^ "Bob"</code>
  <hr>
  <p>We can also get the length of a string:</p>
  <code>String.length "abcdefghijklmnopqstuvwxyz"</code>
  <hr>
  <p>We can also convert a string to lowercase:</p>
  <code>String.lowercase "MARY"</code>
  <hr>
  <h2>Tuple operations</h2>
  <p>A tuple comprises zero or more values, enclosed in parentheses and separated by commas. We can have different types for each element, for example:</p>
  <code>(23, "Bill", false)</code>
  <hr>
  <p>When we have a pair - a tuple with two elements – we can use predefined functions to get the first element:</p>
  <code>fst (23, "Bill")</code>
  <p>Or the second element:</p>
  <code>snd (23, "Bill")</code>
  <hr>

  <div class="inner">
    <button class="act-button" on:click={() => goTo('Welcome')}>Home</button>
    <button class="act-button" on:click={() => goTo('Tutorial2')}>Next</button>
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
