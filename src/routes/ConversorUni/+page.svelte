<script>
    let categorias = [
        { nome: "Peso", icon: "⚖️", id: "peso" },
        { nome: "Comprimento", icon: "📏", id: "comprimento" },
        { nome: "Velocidade", icon: "🚗", id: "velocidade" },
        { nome: "Moeda", icon: "💲", id: "moeda" },
        { nome: "Área", icon: "📍", id: "area" },
        { nome: "Quantidade", icon: "🧪", id: "quantidade" },
        { nome: "Temperatura", icon: "🌡️", id: "temperatura" },
        { nome: "Ângulo", icon: "📐", id: "angulo" },
        { nome: "Pressão", icon: "🌀", id: "pressao" },
        { nome: "Força", icon: "💪", id: "forca" },
        { nome: "Torque", icon: "🔄", id: "torque" },
        { nome: "Densidade", icon: "📦", id: "densidade" }  
    ];
    
    let categoriaSelecionada = "peso";
    let valor = 0;
    let unidadeOrigem = "kg";
    let unidadeDestino = "g";
    let resultado = 0;

    const conversoes = {
        peso: {
            "kg": { "g": 1000, "lb": 2.20462,},
            "g": { "kg": 0.001, "lb": 0.00220462,},
            "lb": { "kg": 0.453592, "g": 453.592,}
        },
        comprimento: {
            "m": { "cm": 100, "km": 0.001,},
            "cm": { "m": 0.01, "km": 0.00001,}
        },
        velocidade: {
            "km/h": { "m/s": 0.277778, "mph": 0.621371,},
            "m/s": { "km/h": 3.6, "mph": 2.23694,},
            "mph": { "km/h": 1.60934, "m/s": 0.44704,}
        },
        moeda: {
            "BRL": { "USD": 0.19, "EUR": 0.18,},
            "USD": { "BRL": 5.25, "EUR": 0.94,},
            "EUR": { "BRL": 5.58, "USD": 1.06,},
            "GBP": { "BRL": 6.42, "USD": 1.22,},
            "JPY": { "BRL": 0.034, "USD": 0.0064}
        },
        area: {
            "m²": { "km²": 0.000001, "ha": 0.0001,},
            "km²": { "m²": 1000000, "ha": 100,},
            "ha": { "m²": 10000, "km²": 0.01}
        },
        quantidade: {
            "mol": { "mmol": 1000,},
            "mmol": { "mol": 0.001}
        },
        temperatura: {
            "°C": { 
                "°F": function(c) { return c * 9/5 + 32; }, 
                "K": function(c) { return c + 273.15; } 
            },
            "°F": { 
                "°C": function(f) { return (f - 32) * 5/9; }, 
                "K": function(f) { return (f - 32) * 5/9 + 273.15; } 
            },
            "K": { 
                "°C": function(k) { return k - 273.15; }, 
                "°F": function(k) { return (k - 273.15) * 9/5 + 32; } 
            }
        },
        angulo: {
            "°": { "rad": 0.0174533, "grad": 1.11111 },
            "rad": { "°": 57.2958, "grad": 63.662 },
            "grad": { "°": 0.9, "rad": 0.015708 }
        },
        pressao: {
            "Pa": { "kPa": 0.001, "MPa": 0.000001},
            "kPa": { "Pa": 1000, "MPa": 0.001},
            "MPa": { "Pa": 1000000, "kPa": 1000}
        },
        forca: {
            "N": { "kN": 0.001, "lbf": 0.224809},
            "kN": { "N": 1000, "lbf": 224.809},
            "lbf": { "N": 4.44822, "kN": 0.00444822}
        },
        torque: {
            "N·m": { "lbf·ft": 0.737562, "kgf·m": 0.101972 },
            "lbf·ft": { "N·m": 1.35582, "kgf·m": 0.138255 },
            "kgf·m": { "N·m": 9.80665, "lbf·ft": 7.23301 }
        },
        densidade: {
            "kg/m³": { "g/cm³": 0.001,},
            "g/cm³": { "kg/m³": 1000,},
        }
    };
    
    function converter() {
        if (categoriaSelecionada === "temperatura") {
            const func = conversoes.temperatura[unidadeOrigem][unidadeDestino];
            resultado = func(valor);
        } else {
            resultado = valor * (conversoes[categoriaSelecionada]?.[unidadeOrigem]?.[unidadeDestino] || 1);
        }
    }
    
    function mudarCategoria(id) {
        categoriaSelecionada = id;
        valor = 0;
        resultado = 0;
        unidadeOrigem = Object.keys(conversoes[id])[0];
        unidadeDestino = Object.keys(conversoes[id])[1];
    }
</script>

<main>
    <header>
        <h1>Conversor de Unidades</h1>
    </header>

    <section class="categoria">
        <h2>Conversores</h2>
        <div class="grid">
            {#each categorias as item}
                <button class="item" on:click={() => mudarCategoria(item.id)}>
                    <span>{item.icon}</span>
                    <p>{item.nome}</p>
                </button>
            {/each}
        </div>
    </section>
    
    <section class="conversor">
        <h2>{categorias.find(c => c.id === categoriaSelecionada)?.nome}</h2>

        <label for="valor">Valor:</label>
        <input id="valor" type="number" bind:value={valor} on:input={converter} />

        <label for="origem">De:</label>
        <select id="origem" bind:value={unidadeOrigem} on:change={converter}>
            {#each Object.keys(conversoes[categoriaSelecionada]) as unidade}
                <option value={unidade}>{unidade}</option>
            {/each}
        </select>

        <label for="destino">Para:</label>
        <select id="destino" bind:value={unidadeDestino} on:change={converter}>
            {#each Object.keys(conversoes[categoriaSelecionada]) as unidade}
                <option value={unidade}>{unidade}</option>
            {/each}
        </select>

        <h2>Resultado: {resultado.toFixed(6)}</h2>
    </section>
</main>

<style>
    main {
        display: flex;
        flex-direction: column;
        align-items: center;
        padding: 20px;
        background: #06458d;
        font-family: Arial, sans-serif;
        max-width: 400px;
        margin: auto;
        border-radius: 12px;
        box-shadow: 0 4px 8px rgba(88, 88, 88, 0.1);
    }

    header {
        text-align: center;
        margin-bottom: 20px;
        color: rgb(199, 207, 207);
    }

    .categoria {
        width: 100%;
        margin-bottom: 20px;
    }

    h2 {
        font-size: 25px;
        color: #def0f5;
        margin-bottom: 10px;
        text-align: center;
    }

    .grid {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        gap: 10px;
    }

    .item {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        background: #1f5ea7;
        padding: 11px;
        border-radius: 8px;
        font-size: 14px;
        text-align: center;
        cursor: pointer;
        transition: 0.2s;
        text-decoration: none;
        color: black;
        border: none;
    }

    span {
        font-size: 24px;
    }

    input, select {
        display: block;
        margin: 10px auto;
        padding: 5px;
    }
</style>