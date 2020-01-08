<script>
	import Tutorial1 from './Tutorial1.svelte'
	import Tutorial2 from './Tutorial2.svelte'
	import Tutorial3 from './Tutorial3.svelte'
	import Tutorial4 from './Tutorial4.svelte'
	import Tutorial5 from './Tutorial5.svelte'
	import Welcome from './Welcome.svelte'
	import Quiz1 from './quiz/Quiz1.svelte'
	import Quiz2 from './quiz/Quiz2.svelte'
	import Quiz3 from './quiz/Quiz3.svelte'
	import Quiz4 from './quiz/Quiz4.svelte'
	import Quiz5 from './quiz/Quiz5.svelte'
	import Score from './quiz/Score.svelte'
	import { tick } from 'svelte';

	let score = 0;
	let step = 'Welcome'
	let answers = {
		1: undefined,
		2: undefined,
		3: undefined,
		4: undefined,
		5: undefined
	}

	const rightAnswers = {
		1: 3,
		2: 3,
		3: 1,
		4: 1,
		5: 3
	}

	const steps = { Tutorial1, Tutorial2, Welcome };

    function changeStep(event) {
        step = steps['Tutorial1'];
    }

		function resetQuiz() {
			score = 0;
			answers = {
					1: undefined,
					2: undefined,
					3: undefined,
					4: undefined,
					5: undefined
				}
		}

		function goTo(event) {
			console.log('go  to ', event.detail.path)
			if(event.detail.path === 'Welcome') {
				resetQuiz()
			}
			step = event.detail.path
		}

		function answered(event) {
			tick().then(() => {
				answers[event.detail.questionNum] = event.detail.responseNum
				if(event.detail.path === 'Score') {
					countScore()
				}
				goTo(event)
			})
		}

		function countScore() {
			const keys = Object.keys(answers)
			const vals = Object.values(answers)
			vals.forEach((val, i) => {
				if(val === rightAnswers[keys[i]]) {
					score = score + 2.5
				} else {
					score = score - 0.5
				}
			})
			console.log('score', score)
			if(score < 0) {
				score = 0
			}
		}
</script>

<main>
<div class="stage">
		{#if step === 'Welcome'}
			<Welcome on:goTo={goTo}></Welcome>
		{:else if step === 'Tutorial1'}
			<Tutorial1 on:goTo={goTo}></Tutorial1>
		{:else if step === 'Tutorial2'}
			<Tutorial2 on:goTo={goTo}></Tutorial2>
		{:else if step === 'Tutorial3'}
			<Tutorial3 on:goTo={goTo}></Tutorial3>
		{:else if step === 'Tutorial4'}
			<Tutorial4 on:goTo={goTo}></Tutorial4>
		{:else if step === 'Tutorial5'}
			<Tutorial5 on:goTo={goTo}></Tutorial5>
		{:else if step === 'Quiz1'}
			<Quiz1 on:answered={answered} answer={answers[1]}></Quiz1>
		{:else if step === 'Quiz2'}
			<Quiz2 on:answered={answered} answer={answers[2]}></Quiz2>
		{:else if step === 'Quiz3'}
			<Quiz3 on:answered={answered} answer={answers[3]}></Quiz3>
		{:else if step === 'Quiz4'}
			<Quiz4 on:answered={answered} answer={answers[4]}></Quiz4>
		{:else if step === 'Quiz5'}
			<Quiz5 on:answered={answered} answer={answers[5]}></Quiz5>
		{:else if step === 'Score'}
			<Score on:goTo={goTo} score={score}></Score>
		{/if}
	</div>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
	.stage {
    position: absolute;
    top: 10%;
    left: 20%;
    width: 60%;
    height: 80%;
    background-color: rgb(48,49,54);
	}

	p {
		color: white
	}
</style>