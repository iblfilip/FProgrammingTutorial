<script>
  import { createEventDispatcher } from 'svelte';
  import { onMount } from 'svelte';

  const dispatch = createEventDispatcher();

  export let answer

  let option1 = '';
  let option2 = '';
  let option3 = '';
  let option4 = '';
  let responseNum = 0;

  const questionNum  = 1;

  onMount(() => {
    if(answer) {
      selectOption(parseInt(answer))
      console.log(parseInt(answer))
    }
  })

  function answerQuestionAndGoTo(path) {
    dispatch('answered', {
      responseNum,
      questionNum,
      path
    })
  }

  function selectOption(num) {
    console.log('option', num)
    if(num === 1) {
      option1 = 'selected'
      option2 = ''
      option3 = ''
    } else if(num === 2) {
      option2 = 'selected'
      option1 = ''
      option3 = ''
    } else if(num === 3) {
      option3 = 'selected'
      option1 = ''
      option2 = ''
    }
    responseNum = num;
  }

</script>
  <div id="uppernavbardiv">
    <div class="headings">
      <div id="upperheading">Quiz</div>
    </div>
  </div>
  <div class="question-block">
    <div class="quest">Question n. 1</div>
    <div class="sent">In the functional programming, which statement is correct?</div>
  </div>
  <div class="options">
    <div on:click={() => selectOption(1)} class="{ option1 ? 'option selected' : 'option'}">Both List and var x are mutable</div>
    <div on:click={() => selectOption(2)} class="{ option2 ? 'option selected' : 'option'}">Both List and var x are immutable</div>
    <div on:click={() => selectOption(3)} class="{ option3 ? 'option selected' : 'option'}">The var x is immutable and the List is mutable</div>
    <div on:click={() => selectOption(4)} class="{ option4 ? 'option selected' : 'option'}">The var x is mutable and the List is immutable</div>
  </div>
  <div class="actions">
    <div class="inner">
      <button class="act-button" on:click={() => answerQuestionAndGoTo('Welcome')}>Back to menu</button>
      <button disabled={responseNum === 0} class="{responseNum > 0 ? 'act-button' : 'act-button disabled'}" on:click={() => answerQuestionAndGoTo('Quiz2')}>Next question</button>
    </div>
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
}

.actions {
  position: absolute;
  left: 10%;
  right: 10%;
  bottom: 10%;
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

.disabled {
  background-color: #c7a172;
  cursor: no-drop;

}

.question-block {
  display: flex;
  padding: 50px 0 50px 0;
  flex-direction: column;
  align-items: flex-start;
  color: white;
  margin-left: auto;
  margin-right: auto;
  width: 80%;
}

.quest {
  font-size: 30px;
}

.sent {
  padding-top: 10px;
}

.options {
  margin-left: auto;
  margin-right: auto;
  width: 70%;
}

.option {
  background-color: white; /* Green */
  border: 1px;
  border-radius: 10px;
  color: black;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  margin: 10px;
  font-size: 16px;
  width: 100%;
  cursor: pointer;
}

.selected {
  background-color: #dc9135;
  color: white;
}
</style>