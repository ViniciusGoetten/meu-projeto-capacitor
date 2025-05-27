<script>
    const tarefasAFazer = $state(['estender a roupa', 'escovar os dentes', 'dar comida para os']);
    const tarefasConcluidas = $state([]);
    let tarefaNova = $state();
    let tarefaEditandoIndice = $state();
    let tarefaEditando = $state();
  
    function adicionarTarefa() {
        if (tarefaNova.trim()) {
            tarefasAFazer.push(tarefaNova);
            tarefaNova = '';
        }
    }
  
    function excluirTarefa(lista, i) {
        lista.splice(i, 1);
    }
  
    function editarTarefa(i) {
        tarefaEditandoIndice = i;
        tarefaEditando = tarefasAFazer[i];
    }
  
    function salvarTarefa(i) {
        tarefasAFazer[i] = tarefaEditando;
        tarefaEditandoIndice = null;
    }
  
    function cancelarEdicao() {
        tarefaEditandoIndice = null;
        tarefaEditando = '';
    }
  
    function marcarComoConcluida(i) {
        tarefasConcluidas.push(tarefasAFazer[i]);
        tarefasAFazer.splice(i, 1);
    }
  
    function desmarcarComoConcluida(i) {
        tarefasAFazer.push(tarefasConcluidas[i]);
        tarefasConcluidas.splice(i, 1);
    }
  </script>
  
  <div class="container">
    <h2 class="titulo">Lista de Tarefas</h2>
    <p class="input-tarefa">
        <input 
            class="input-nova-tarefa" 
            placeholder="Digite a tarefa..." 
            bind:value={tarefaNova} 
            
        />
        <button class="btn btn-adicionar" onclick={adicionarTarefa}>➕</button>
    </p>
  
    <h3 class="subtitulo">Tarefas a Fazer</h3>
    <ul class="lista">
        {#each tarefasAFazer as tarefa, i}
            <li class="item">
                {#if tarefaEditandoIndice == i}
                    <input class="input-edicao" bind:value={tarefaEditando} />
                    <button class="btn btn-salvar" onclick={() => salvarTarefa(i)}>💾</button>
                    <button class="btn btn-cancelar" onclick={cancelarEdicao}>❌</button>
                {:else}
                    {tarefa}
                    <div class="botoes">
                        <button class="btn btn-editar" onclick={() => editarTarefa(i)}>✏</button>
                        <button class="btn btn-excluir" onclick={() => excluirTarefa(tarefasAFazer, i)}>🗑</button>
                        <button class="btn btn-concluido" onclick={() => marcarComoConcluida(i)}>✔</button>
                    </div>
                {/if}
            </li>
        {/each}
    </ul>
  
    <h3 class="subtitulo">Tarefas Concluídas</h3>
    <ul class="lista lista-concluidas">
        {#each tarefasConcluidas as tarefa, i}
            <li class="item">
                {tarefa}
                <div class="botoes">
                    <button class="btn btn-excluir" onclick={() => excluirTarefa(tarefasConcluidas, i)}>🗑</button>
                    <button class="btn btn-retornar" onclick={() => desmarcarComoConcluida(i)}>↩</button>
                </div>
            </li>
        {/each}
    </ul>
  </div>
  
  <style>
    body {
      font-family: 'Times New Roman', Times, serif;
        background-color: #000000;
        color: #333;
        margin: 0;
        padding: 0;
    }
  
    .container {
        max-width: 600px;
        margin: 40px auto;
        padding: 20px;
        background-image: url('viado.jpg'); 
        background-size: cover; 
          background-attachment: fixed; 
        box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    }
  
    .titulo {
        text-align: center;
        color: #ffffff;
        margin-bottom: 20px;
    }
  
    .subtitulo {
        color: #ffffff;
        margin-top: 30px;
        margin-bottom: 10px;
        font-size: 18px;
    }
  
    .input-tarefa {
        display: flex;
        justify-content: center;
        align-items: center;
        margin-bottom: 20px;
    }
  
    .input-nova-tarefa {
        width: 80%;
        padding: 10px;
        border: 1px solid #ddd;
        border-radius: 4px;
        font-size: 16px;
    }
  
    .btn {
        margin-left: 10px;
        padding: 8px 12px;
        border: none;
        border-radius: 4px;
        cursor: pointer;
        font-size: 16px;
    }
  
    .btn-adicionar {
        background-color: #ffffff;
        color: #000000;
    }
  
    .lista {
        list-style: none;
        padding: 0;
    }
  
    .item {
        display: flex;
        justify-content: space-between;
        align-items: center;
        background: #f9f9f9;
        margin-bottom: 10px;
        padding: 10px;
        border: 1px solid #8b8b8b;
        border-radius: 4px;
    }
  
    .botoes {
        display: flex;
        gap: 5px;
    }
  
    .btn-editar {
        background-color: #000000;
        color: #fff;
    }
  
    .btn-excluir {
        background-color: #000000;
        color: #fff;
    }
  
    .btn-concluido {
        background-color: #00ff15;
        color: #fff;
    }
  
    .btn-retornar {
        background-color: #000000;
        color: #fff;
    }
  
    .input-edicao {
        flex-grow: 1;
        padding: 5px;
        border: 1px solid #000000;
        border-radius: 4px;
        margin-right: 20px;
    }
  </style>
  
  <head>
    <style>
      body {
        background-image: url('viado.jpg'); 
        background-size: cover; 
        background-position: center;
        background-attachment: fixed; 
        font-family: 'Times New Roman', Times, serif;
      }
    </style>
  </head>
  