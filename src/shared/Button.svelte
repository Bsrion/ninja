<script>

let  {type ='primary', flat = false, inverse = false} = $props();

</script>

<!-- svelte-ignore slot_element_deprecated -->
<button class={type} class:flat={flat} class:inverse={inverse}>
    <slot></slot>
</button>

<style>
.primary{
background: #d91b42;
color:white;
}
.secondary{
background: #45c496;
color:white;
}


button{
    border: 0;
    cursor: pointer;
    border-radius: 6px;
    padding: 8px 12px;
    font-weight: bold;
    box-shadow: 1px 2px 3px rgba(0,0,0,0.2);
}
.secondary.inverse{
    color:#45c496;
    background: white;
    border: 2px solid #45c496
}
.primary.inverse{
    color:#d91b42;
    background: white;
    border: 2px solid #d91b42
}
.flat{
    box-shadow: none;
}

</style>