<script>
    import {createEventDispatcher} from "svelte";
    export let text="";
    export let correctAnswer;
    export let possibleAnswers;
    let selectedAnswer;
    let state;
    const shuffle=(array)=>{
        return array.sort(()=>Math.random()-0.5);
    };
    const selectAnswer =(i)=>{
        selectedAnswer=i;
        if (selectedAnswer===correctIndex)
            state="correct";
        else
            state="wrong";     
    }
    possibleAnswers=shuffle(possibleAnswers);
    let correctIndex=possibleAnswers.indexOf(correctAnswer);
</script>
<div>
    {#if state==="correct"}
        <h2 style="color:green">{text}</h2>
    {:else if state ==="wrong"}
        <h2 style="color:red">{text}</h2>
    {:else}
        <h2>{text}</h2>
    {/if}
    {#each possibleAnswers as pa}
        <button on:click={() => selectedAnswer(i)}>{pa}</button>
    {/each}
    
</div>