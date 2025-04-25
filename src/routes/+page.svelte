<script>
// @ts-nocheck

	import CreatePollForm from '../component/CreatePollForm.svelte';

// @ts-nocheck

import Footer from '../component/footer.svelte';
import Header from '../component/header.svelte';
import PollList from '../component/pollList.svelte';
import Tabs from '../shared/tabs.svelte';

let count = $state(0);
let multiplay = $derived(count * 2);
let activeItem = $state('current polls')
let items =  ['current polls', 'Add New Poll'];
const toggleTab = (e) => {
    activeItem = e.detail;
    console.log(activeItem);
}
let polls = $state([])
const handelAdd = (e)=>{
    const poll = e.detail;
    polls = [poll, ...polls];
    activeItem = 'current polls';
}
const deletCardFromPolls = (e) => {
    const id = e.detail;
    polls = polls.filter(poll => poll.id !== id);
}
</script>

<Header />

<maim>

    <Tabs {activeItem} {items} on:tabChange={toggleTab}/>
    {#if activeItem === 'current polls'}
        <PollList {polls} on:delete = {deletCardFromPolls}/>
   {:else if activeItem === 'Add New Poll'}
    <CreatePollForm on:add = {handelAdd} />
    {/if}
</maim>
<Footer />

<style>

    maim {
        display: block;
        padding: 20px;
        color: black;
    }
 
</style>