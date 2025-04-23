<script>
// @ts-nocheck

	import Button from "../shared/Button.svelte";
    import { createEventDispatcher } from "svelte";
    let dispatch = createEventDispatcher();

let errors = $state({question: '', answerA: '', answerB: ''})
let fields = $state({question: '', answerA: '', answerB: ''});
let valid = $state(false);
const submitHandler = (e)=>{
e.preventDefault();;
valid = true;
if(fields.question.trim().length < 5){
    valid = false;
    errors.question = ' question must be at least 5 characters long '
}else{
    errors.question = '';
}
if(fields.answerA.trim().length < 1){
    valid = false;
    errors.answerA = ' answerA can`t be empty '
}else{
    errors.answerA = '';
}
if(fields.answerB.trim().length < 1){
    valid = false;
    errors.answerB = ' answerB can`t be empty '
}else{
    errors.answerB = '';
}
if(valid){
let poll = {...fields, voteA: 0, voteB: 0, id: Math.random()};
dispatch('add', poll);
}}
</script>

<form onsubmit={submitHandler}>
    <div class="formfield">
<label for='question'>Poll Question</label>
<input type="text" id='question' bind:value={fields.question}>
<div class='error'>{errors.question}</div>
    </div>
    <div class="formfield">
<label for='answer-a'>Answer-a</label>
<input type="text" id='answer-a' bind:value={fields.answerA}>
<div class='error'>{errors.answerA}</div>
    </div>
    <div class="formfield">
<label for='answer-b'>Answer-b</label>
<input type="text" id='answer-b' bind:value={fields.answerB}>
<div class='error'>{errors.answerB}</div>
    </div>
    <Button type = 'secondary' flat={true}>
        Add Poll
    </Button>
</form>


<style>
form{
    width: 400px;
    margin: 0 auto;
    color: gray;
    text-align: center;
}
.formfield{
    margin: 18px auto;
}
input{
    width: 100%;
    border-radius: 6px;
    min-height: 1.5rem;
    padding: 2px 10px;
    border: solid 0.5px lightgray;
}

label{
margin: 10px auto;
text-align: left;
}
.error{
    color: #d91b42;;
    font-weight: bold;
    font-size: 12px;
}

</style>