<script>
// @ts-nocheck

	import PollDetails from "./pollDetails.svelte";
    import { createEventDispatcher } from "svelte";
    let dispatch = createEventDispatcher();

    let {polls = []} =  $props();

const deletePollFroList = (e) => {
        const id = e.detail;
        dispatch('delete', id);
    }
</script>



<div class="poll-list">
    {#each polls as poll (poll.id)}
    <PollDetails {poll} on:delete = {deletePollFroList}/>
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