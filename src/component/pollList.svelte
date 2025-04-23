<script>
	import PollDetails from "./pollDetails.svelte";

    let {polls = []} =  $props();

</script>



<div class="poll-list">
    {#each polls as poll (poll.id)}
    <PollDetails {poll}/>
    {/each}
</div>



<style>

.poll-list{
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    grid-gap: 20px;
    color: gray;
}
</style>