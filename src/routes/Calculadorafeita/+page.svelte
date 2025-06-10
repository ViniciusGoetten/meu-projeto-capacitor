<script>
  let display = '';

  function clear() {
    display = '';
  }

  function calc() {
    try {
      display = eval(display.replace('x', '*')).toString();
    } catch (error) {
      display = 'Error';
    }
  }

  function press(c) {
    display += c;
  }

  function changeSign() {
    try {
      display = (parseFloat(display) * -1).toString();
    } catch (error) {
      display = 'Error';
    }
  }

  function percentage() {
    try {
      display = (parseFloat(display) / 100).toString();
    } catch (error) {
      display = 'Error';
    }
  }

  function square() {
    try {
      display = (parseFloat(display) ** 2).toString();
    } catch (error) {
      display = 'Error';
    }
  }

  function squareRoot() {
    try {
      display = Math.sqrt(parseFloat(display)).toString();
    } catch (error) {
      display = 'Error';
    }
  }

  function backspace() {
  display = display.slice(0, -1);
}

  function logBase10() {
    try {
      display = Math.log10(parseFloat(display)).toString();
    } catch (error) {
      display = 'Error';
    }
  }

  function modulo() {
    try {
      const divisor = prompt("Digite o divisor:");
      if (divisor !== null) {
        display = (parseFloat(display) % parseFloat(divisor)).toString();
      }
    } catch (error) {
      display = 'Error';
    }
  }
</script>

<style>

  input.display {
    width: 100%;
    font-size: 2rem;
    font-weight: 700;
    padding: 0.75rem 1rem;
    border-radius: 0.5rem;
    border: 1px solid #324664;
    margin-bottom: 1.5rem;
    text-align: right;
    color: #172749;
  }

  .buttons-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-auto-rows: 3.5rem;
    gap: 0.5rem;
  }

  button {
    font-weight: 600;
    border-radius: 0.5rem;
    border: none;
    cursor: pointer;
    user-select: none;
    font-size: 1.25rem;
    padding: 0.75rem 0;
    transition: background-color 0.3s, transform 0.2s;
    box-shadow: 0 1px 3px rgb(0 0 0 / 0.1);
  }


  button:focus-visible {
    outline: 2px solid #3b82f6;
    outline-offset: 2px;
  }

  .btn-clear {
    background: #e4c6c6;
    color: white;
  }

  .btn-clear:hover {
    background: #d3baba;
  }

  .btn-operator {
    background: #0e2b5a;
    color: rgb(255, 255, 255);
  }

  .btn-operator:hover {
    background: #213768;
  }

  .btn-secondary {
    background: #38589c;
    color: white;
  }

  .btn-secondary:hover {
    background: #7d8897;
  }

  .btn-number {
    background: #e5e7eb;
    color: #111827;
  }

  .btn-number:hover {
    background: #d1d5db;
  }

  .btn-plus {
    grid-row: span 2;
    height: 100%;
  }
</style>

<div class="calculator">
  <input class="display" readonly value={display} />
  <div class="buttons-grid">

    <button class="btn-clear" onclick={clear}>C</button>
    <button class="btn-secondary" onclick={() => press('(')}>(</button>
    <button class="btn-secondary" onclick={() => press(')')}>)</button>
    <button class="btn-operator" onclick={() => press('/')}>/</button>

    <button class="btn-number" onclick={() => press('7')}>7</button>
    <button class="btn-number" onclick={() => press('8')}>8</button>
    <button class="btn-number" onclick={() => press('9')}>9</button>
    <button class="btn-operator" onclick={() => press('x')}>×</button>

    <button class="btn-number" onclick={() => press('4')}>4</button>
    <button class="btn-number" onclick={() => press('5')}>5</button>
    <button class="btn-number" onclick={() => press('6')}>6</button>
    <button class="btn-operator" onclick={() => press('-')}>-</button>

    <button class="btn-number" onclick={() => press('1')}>1</button>
    <button class="btn-number" onclick={() => press('2')}>2</button>
    <button class="btn-number" onclick={() => press('3')}>3</button>
    <button class="btn-operator btn-plus" onclick={() => press('+')}>+</button>

    <button class="btn-number" onclick={() => press('0')}>0</button>
    <button class="btn-number" onclick={() => press('.')}>.</button>
    <button class="btn-operator" onclick={calc}>=</button>

    <button class="btn-secondary" onclick={changeSign}>±</button>
    <button class="btn-secondary" onclick={percentage}>%</button>
    <button class="btn-secondary" onclick={square}>x²</button>
    <button class="btn-secondary" onclick={squareRoot}>√</button>

    <button class="btn-secondary" onclick={logBase10}>log</button>
    <button class="btn-secondary" onclick={modulo}>\</button>
    <button class="btn-secondary" onclick={backspace}>⌫</button>
  </div>
</div>