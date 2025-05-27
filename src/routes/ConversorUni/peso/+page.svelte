<script>
    let aceleracao, massa, forca;
  
    function calcularforca() {
      forca = massa * aceleracao;
    }
  </script>
  
  
  
  
  <h1>Calculadora de Força</h1>
  
  Aceleração:
  <input type="number" min="0" bind:value={aceleracao} />
  <br />
  
  Massa:
  <input type="number" min="0" bind:value={massa} />
  <br />
  
  <button onclick={calcularforca}> Calcular Força</button>
  
  <p>A força é: {forca || '...'}</p>
  
  {#if forca < 2000}
    <div class="verde"><p>Pode voar tranquilamente 😁</p></div>
  {:else if forca >= 2000 && forca <= 4000}
    <div class="amarelo"><p>Tome cuidado 😬</p></div>
  {:else if forca > 4000}
    <div class="vermelho"><p>Depois não te diga que eu não avisei 😢</p></div>
  {/if}
  
  <style>
    .verde {
      color: green;
    }
  
    .amarelo {
      color: yellow;
    }
  
    .vermelho {
      color: red;
    }
  </style>
  
  