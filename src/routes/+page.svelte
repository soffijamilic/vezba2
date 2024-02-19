<script>
    import { onMount } from "svelte";
    import Question from "./Question.svelte";
    let question;
    const question;


    const getQuestion=async()=>{
        const res= await fetch("https://opentdb.com/api.php?amount=1&category=27&difficulty=easy&type=multiple")
        let data = await res.json();

    }
    onMount(getQuestion);
</script>
<h1>My quiz</h1>
{#if question !== undefined}
<Question
    text={question.question}
    correctAnswer{question.correct_answer}
    possibleAnswers{[...question.incorrect_answers,question.correct_answer]}
    on:answers={getQuestion}
/>
{/if}
