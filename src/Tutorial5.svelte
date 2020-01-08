<div id="uppernavbardiv">
  <div class="headings">
    <div id="upperheading">Pattern Matching</div>
  </div>
</div>
<div class="content">
  <h2>Pattern-matching on integers</h2>
  <p>OCaml has a powerful feature called pattern-matching. For integers, pattern-matching is similar to case switches in other languages (_ corresponds to the default case). Each case is handled in chronological order:</p>
  <code>let string_of_int x = match x with | 0 -> "zero" | 1 -> "one" | 2 -> "two" | _ -> "many"</code>
  <hr>
  <p>Pattern matching in this case is done on the last function argument, hence this function can be rewritten as:</p>
  <code>let string_of_int2 = function | 0 -> "zero" | 1 -> "one" | 2 -> "two" | _ -> "many"</code>
  <hr>
  <h2>Pattern-matching on chars</h2>
  <p>Pattern-matching on characters can be done with a special syntax to denote character ranges:</p>
  <code>let is_capital = function | 'a' .. 'z' -> false | 'A' .. 'Z' -> true | _ -> failwith "Not a valid letter"</code>
  <hr>
  <h2>Pattern-matching on tuples</h2>
  <p>Pattern-matching is also possible on tuples:</p>
  <code>let fit str len = match (str,len) with | ("foo", 51) -> true | ("bar", 51) -> true | (_ , 42) -> false | _ -> (String.length str) = len</code>
  <hr>
  <p>It is possible to omit the first occurrences of the value in case multiple patterns return a similar value:</p>
  <code>let fit str len = match (str,len) with | ("foo", 51) | ("bar", 51) -> true | (_ , 42) -> false | _ -> (String.length str) = len</code>
  <hr>
  <h2>Pattern-matching on list</h2>
  <p>The real power of pattern-matching comes when we begin using more structured values, when we begin giving a name to matched patterns. For example, a list is either empty [] or has a head and a tail, denoted by the pattern h::t where h and t are bound to the matched patterns:</p>
  <code>let head = function | [] -> failwith "empty list" | h::t -> h</code>
  <hr>
  <p>More complex patterns can be written, for example to look at the head of the tail:</p>
  <code>let second_element = function | [] -> failwith "the list is empty" | [_] -> failwith "the list contains only one element" | _::e::_ -> e</code>
  <hr>
  <h2>Pattern-matching on arrays</h2>
  <p>Furthermore, we can pattern match on arrays:</p>
  <code>let has_size_two = function | [| _; _ |] -> true | _ -> false</code>
  <hr>

  <div class="inner">
    <button class="act-button" on:click={() => goTo('Tutorial3')}>Back</button>
    <button class="act-button" on:click={() => goTo('Quiz1')}>Test skills in Quiz</button>
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
    height: 93%;
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
