<script>
  
    let promise = $state();
    let questionario = $state([]);
    let respostas = $state([]);
    let respondeu = $state(false);
   
    function gerarNovoQuiz() {
        respondeu = false;
        promise = fetch('https://opentdb.com/api.php?amount=5&category=9&type=multiple')
            .then((response) => response.json())
            .then((data) => {
                questionario = data.results;
                for (const pergunta of questionario) {
                    const i = Math.floor(Math.random() * pergunta.incorrect_answers.length + 1);
                    pergunta.incorrect_answers.splice(i, 0, pergunta.correct_answer);
                }
            });
    }
   
    function verificarRespostas() {
        respondeu = true;
        let acertos = 0;
        for (let i = 0; i < questionario.length; i++) {
            if (respostas[i] === questionario[i].correct_answer) {
                acertos++;
            }
        }
        alert(`Você acertou ${acertos} de ${questionario.length} questões!`);
    }
</script>

<div class="container">
    <button class="btn btn-info" onclick={gerarNovoQuiz}>Gerar novo quiz</button>
   
    {#await promise}
        <p>Gerando novo questionário...</p>
    {:then}
        <ol class="quiz-list">
            {#each questionario as pergunta, i}
                <h4><li>{@html pergunta.question}</li></h4>
                {#each pergunta.incorrect_answers as alternativa}
                    <div class="form-check">
                        <input class="form-check-input" type="radio" id={alternativa} bind:group={respostas[i]} value={alternativa} oninput={() => (respondeu = false)} />
                        <label class="form-check-label" for={alternativa}>{@html alternativa}</label>
   
                        {#if respondeu && alternativa == respostas[i]}
                            {#if alternativa == pergunta.correct_answer}
                                <span class="badge bg-success">Correto</span>
                            {:else}
                                <span class="badge bg-danger">Incorreto</span>
                            {/if}
                        {/if}
                    </div>
                {/each}
            {/each}
        </ol>
        <button onclick={verificarRespostas} class="btn btn-success btn-block">Confirmar!</button>
    {:catch error}
        <p style="color: red">{error.message}</p>
    {/await}
</div>

<style>
    /* Estilos gerais */
    .container {
        max-width: 100%;
        padding: 15px;
    }

    .quiz-list {
        list-style-type: none;
        padding: 0;
    }

    h4 {
        font-size: 1.2em;
    }

    .form-check {
        margin-bottom: 10px;
    }

    .form-check-label {
        font-size: 1em;
    }

    .btn-block {
        width: 100%;
    }

    /* Estilos responsivos */
    @media (max-width: 768px) {
        h4 {
            font-size: 1em;
        }

        .btn {
            font-size: 1em;
            padding: 12px;
        }

        .form-check {
            font-size: 1em;
        }
    }

    /* Para telas muito pequenas, como smartphones */
    @media (max-width: 480px) {
        .container {
            padding: 10px;
        }

        .btn {
            font-size: 1.2em;
            padding: 15px;
        }

        h4 {
            font-size: 1em;
        }

        .form-check-input {
            margin-right: 10px;
        }
    }
</style>