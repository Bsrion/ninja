<script>
// @ts-nocheck
    import Card from '../shared/card.svelte'; 
let {poll = {}} = $props();
let totalVotes = $derived(poll.voteA + poll.voteB)

</script>
<Card>
    <div class="poll">
        <h3>{poll.question}</h3>
        <p>Total votes: {totalVotes}</p>
        <div class="answer" onclick={()=>{poll.voteA++}}>
            <div class="percent percent-a"></div>
            <span>{poll.answerA} ({poll.voteA})</span>
    </div>
        <div class="answer" onclick={()=>{poll.voteB++}}>
            <div class="percent percent-b"></div>
            <span>{poll.answerB} ({poll.voteB})</span>
        </div>
    </div>
</Card>

<style>
h3{
    margin: 0 auto;
    color:#555;
}
p{
    margin-top: 6px;
    font-size: 14px;
    color: #aaa;
    margin-bottom: 30px;
}
.answer{
    background: #fafafa;
    cursor: pointer;
    margin: 10px auto;
    position: relative;
}
.answer:hover{
    opacity: 0.6;
}
span{
    display: inline-block;
    padding: 10px;
}
</style>