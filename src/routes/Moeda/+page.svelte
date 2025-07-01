<script>
    let moedas = [
        { nome: 'Dólar americano', código: 'USD' },
        { nome: 'Real brasileiro', código: 'BRL' },
        { nome: 'Euro', código: 'EUR' },
        { nome: 'Libra esterlina', código: 'GBP' },
        { nome: 'Iene japonês', código: 'JPY' },
        { nome: 'Peso argentino', código: 'ARS' }
    ];

    let código1 = $state(moedas[0].código);
    let código2 = $state(moedas[1].código);
    let valor1 = $state(0);
    let valor2 = $state(0);
    let moedaPadrao = $state(null);
    let ultimaAtualizacao = $state('');

    async function mudarMoeda() {
        const resposta = await fetch(`https://open.er-api.com/v6/latest/${código1}`);
        const dados = await resposta.json();
        moedaPadrao = dados;
        ultimaAtualizacao = new Date(dados.time_last_update_utc).toLocaleString();
        converterDe();
    }

    function converterDe() {
        if (moedaPadrao && moedaPadrao.rates) {
            valor2 = (valor1 * moedaPadrao.rates[código2]).toFixed(2);
        }
    }

    function converterPara() {
        if (moedaPadrao && moedaPadrao.rates) {
            valor1 = (valor2 / moedaPadrao.rates[código2]).toFixed(2);
        }
    }

    function inverterMoedas() {
        [código1, código2] = [código2, código1];
        [valor1, valor2] = [valor2, valor1];
        mudarMoeda();
    }

    mudarMoeda();
</script>

<style>


  .container {
    margin: 80px auto;
    background: #fff;
    padding: 40px 30px;
    border-radius: 16px;
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
    text-align: center;
    max-width: 720px;
  }

  h1 {
    color: #007bff;
    font-size: 32px;
    margin-bottom: 30px;
  }

  .input-group {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 12px;
    flex-wrap: wrap;
    margin-bottom: 20px;
  }

  select, input {
    padding: 10px;
    font-size: 16px;
    border-radius: 8px;
    border: 1px solid #ccc;
    max-width: 150px;
    width: 100%;
  }

  input[type="number"] {
    max-width: 120px;
  }

  .btn {
    background-color: #f0f0f0;
    border: 1px solid #ccc;
    padding: 10px 14px;
    font-size: 20px;
    border-radius: 8px;
    cursor: pointer;
    transition: background 0.3s ease;
  }

  .btn:hover {
    background-color: #dcdcdc;
  }

  .styled-button {
    width: 100%;
    padding: 14px;
    font-size: 18px;
    color: white;
    background-color: #007bff;
    border: none;
    border-radius: 50px;
    box-shadow: 0 4px 10px rgba(0, 123, 255, 0.3);
    cursor: pointer;
    transition: background-color 0.3s, transform 0.2s;
  }

  .styled-button:hover {
    background-color: #0056b3;
    transform: translateY(-2px);
  }

  @media (max-width: 600px) {
    .input-group {
      flex-direction: column;
    }

    select, input, .btn {
      max-width: 100%;
    }
  }
</style>

<div class="container">
  <h1>Cotação de Moedas</h1>
  <div class="input-group">
    <select bind:value={código1} onchange={mudarMoeda}>
      {#each moedas as moeda}
        <option value={moeda.código} title={moeda.nome}>{moeda.código}</option>
      {/each}
    </select>

    <input type="number" placeholder="0,00" bind:value={valor1} oninput={converterDe} />

    <button class="btn" type="button" onclick={inverterMoedas}>⇄</button>

    <input type="number" placeholder="0,00" bind:value={valor2} oninput={converterPara} />

    <select bind:value={código2} onchange={converterPara}>
      {#each moedas as moeda}
        <option value={moeda.código} title={moeda.nome}>{moeda.código}</option>
      {/each}
    </select>
  </div>

  <a href="/paginas/aba">
    <button class="styled-button">Voltar</button>
  </a>
</div>