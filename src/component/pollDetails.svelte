<script>
// @ts-nocheck
    import Card from '../shared/card.svelte'; 
let {poll = {}} = $props();
let totalVotes = $derived(poll.voteA + poll.voteB);
let firstanswer = $derived(Math.floor(poll.voteA / totalVotes * 100));
let secondanswer = $derived(Math.floor(poll.voteB / totalVotes * 100));

</script>
<Card>
    <div class="poll">
        <h3>{poll.question}</h3>
        <p>Total votes: {totalVotes}</p>
        <!-- svelte-ignore a11y_no_static_element_interactions -->
        <div class="answer" onclick={()=>{poll.voteA++}} onkeydown={(e)=>{if(e.key === 'Enter'){poll.voteA++}}}>
            <div class="percent percent-a" style="width:{firstanswer}%"></div>
            <span>{poll.answerA} ({poll.voteA})</span>
    </div>
        <!-- svelte-ignore a11y_no_static_element_interactions -->
        <div class="answer" onclick={()=>{poll.voteB++}} onkeydown={(e)=>{if(e.key === 'Enter'){poll.voteB++}}}>
            <div class="percent percent-b" style="width:{secondanswer}%"></div>
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
.percent{
    height: 100%;
    position: absolute;
    box-sizing: border-box;
}
.percent-a{
    background-color: rgba(217, 27 , 66, 0.2);
    border-left: solid 4px rgba(217, 27 , 66, 1);
}
.percent-b{
    background-color: rgba(69, 196 , 50, 0.2);
    border-left: solid 4px rgba(69, 196 , 50, 1);
}
</style>