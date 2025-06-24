<script>
    import { page } from '$app/stores';
    import { dicionario } from '$lib/dicio/dicionario';
  
    const palavra = $page.params.palavra.toLowerCase();
    const termo = dicionario.find(item => item.palavra.toLowerCase() === palavra);
  </script>
  

  
  {#if termo}
    <div>
      <h1>{termo.palavra}</h1>
      <ul>
        {#each termo.definicoes as definicao}
          <li>{definicao}</li>
        {/each}
      </ul>
      <a href="/dicionario">Voltar</a>
    </div>
  {:else}
    <div>
      <p>Palavra não encontrada!</p>
      <a href="/dicionario">Voltar</a>
    </div>
  {/if}
  