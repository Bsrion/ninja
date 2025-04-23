<script>
let {items, activeItem} = $props();
import {createEventDispatcher} from 'svelte';
let dispatch = createEventDispatcher();
</script>

<div class="tabs">
<ul>
{#each items as item}
<li>
    <button onclick={() => dispatch('tabChange', item)}
            onkeydown={(e) => {
                if (e.key === 'Enter') {
                    dispatch('tabChange', item);
                }
            }}
            class:active={item === activeItem}>
        {item}
    </button>
</li>
{/each}
</ul>

</div>

<style>
    .tabs{
    margin-bottom: 40px;
    }
ul{
    display: flex;
    justify-content: center;
    padding: 0px;
    list-style-type: none;
}
li{
    margin: 0px 20px;
    padding: 0px;
    font-size: 18px;
    color: #555;

}

.active{
    color: d91b42;
    border-bottom: solid 2px #d91b42;
    padding-bottom: 8px;
}
button{
    background: none;
    border: none;
    color: inherit;
    font: inherit;
    cursor: pointer;
    outline: inherit;
}

</style>