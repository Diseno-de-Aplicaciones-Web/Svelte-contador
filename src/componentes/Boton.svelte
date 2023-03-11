<button on:click={manejadorClick}>

    {texto} ({numeroDeClicks})
    
</button>

<script>

    export let texto
    export let alClickar

    let numeroDeClicks = 0

    function manejadorClick() {
        numeroDeClicks++
        alClickar()
    }

</script>