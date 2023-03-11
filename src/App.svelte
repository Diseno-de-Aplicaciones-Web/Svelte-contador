<main>
  <div id="contador">{contador}</div>
  <Boton texto="-" alClickar={manejadorDecremento}/>
  <Boton texto="+" alClickar={manejadorIncremento}/>
  <Boton texto="Auto" alClickar={manejadorAuto}/>
</main>

<script>
  import { afterUpdate } from "svelte";

  import Boton from "./componentes/Boton.svelte"

  let contador = 0
  let auto = false
  let temporizador

  function manejadorIncremento() {
    contador++
  }

  function manejadorDecremento() {
    contador--
  }

  function manejadorAuto() {
    auto = !auto
  }

  function actualizarIncremento() {
    clearTimeout(temporizador)
    if (auto) temporizador = setTimeout(manejadorIncremento,1000)
  }

  $: if (auto) actualizarIncremento()

  afterUpdate(
    actualizarIncremento
  )

</script>

<style>
  #contador {
    font-size: 6rem;
  }
</style>