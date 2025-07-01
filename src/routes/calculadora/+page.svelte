<script>
    let display = '';
     function backspace() {
        display = display.slice(0, -1);
     }
    function press(c) {
        display += c;
    }
    
    function calc() {
            display = eval(display);
       
    }
    
    function clear() {
        display = '';
    }
    
    function invertSignal() {
        
            display = eval(display) * -1;
       
    }
    
    function square() {
        
            const val = eval(display);
            display = val * val;
       
    }
    
    function sqrt() {
        
            const val = eval(display);
            display = Math.sqrt(val);
        
    }
    
    function round() {
        
            const val = eval(display);
            display = Math.round(val);
        
    }
    
    function log10() {
        
            const val = eval(display);
            display = Math.log10(val);
        
    }
    
    </script>
    
    <div class="text-center mt-3">
        <input class = "form-control form-control-lg" readonly bind:value={display}/>
    <table class="table table-sm table-borderless">
        <tbody>
            <tr>
                <td><button class="btn btn-outline-danger w-100" onclick={() => clear()}>C</button></td>
                <td><button class="btn btn-outline-dark w-100" onclick={() => press('(')}>&lpar;</button></td>
                <td><button class="btn btn-outline-dark w-100" onclick={() => press(')')}>&rpar;</button></td>
                <td><button class="btn btn-outline-dark w-100" onclick={() => press('/')}>/</button></td>
                <td><button class="btn btn-outline-danger w-100" onclick={() => backspace('')}>⌫</button></td>
                <td><button class="btn btn-outline-dark w-100" onclick={round}>arr</button></td>
            </tr>
            <tr>
                <td><button class="btn btn-outline-primary w-100" onclick={() => press('7')}>7</button></td>
                <td><button class="btn btn-outline-primary w-100" onclick={() => press('8')}>8</button></td>
                <td><button class="btn btn-outline-primary w-100" onclick={() => press('9')}>9</button></td>
                <td><button class="btn btn-outline-dark w-100" onclick={() => press('*')}>x</button></td>
                <td><button class="btn btn-outline-dark w-100" onclick={sqrt}>√</button></td>
                <td><button class="btn btn-outline-dark w-100" onclick={square}>x²</button></td>
            </tr>
            <tr>
                <td><button class="btn btn-outline-primary w-100" onclick={() => press('4')}>4</button></td>
                <td><button class="btn btn-outline-primary w-100" onclick={() => press('5')}>5</button></td>
                <td><button class="btn btn-outline-primary w-100" onclick={() => press('6')}>6</button></td>
                <td><button class="btn btn-outline-dark w-100" onclick={() => press('-')}>-</button></td>
                <td><button class="btn btn-outline-dark w-100" onclick={() => press('%')}>%</button></td>
                <td><button class="btn btn-outline-dark w-100" onclick={square}>cos</button></td>
            </tr>
            <tr>
                <td><button class="btn btn-outline-primary w-100" onclick={() => press('1')}>1</button></td>
                <td><button class="btn btn-outline-primary w-100" onclick={() => press('2')}>2</button></td>
                <td><button class="btn btn-outline-primary w-100" onclick={() => press('3')}>3</button></td>
                <td rowspan="2" style="height: 0;">
                <button class="btn btn-outline-dark w-100 h-100" onclick={() => press('+')}>+</button></td>
                <td><button class="btn btn-outline-dark w-100" onclick={invertSignal}>+/-</button></td>
                <td><button class="btn btn-outline-dark w-100" onclick={''}>sen</button></td>
            </tr>
            <tr>
                <td><button  class="btn btn-outline-primary w-100" onclick={() => press('0')}>0</button></td>
                <td><button  class="btn btn-outline-dark w-100" onclick={() => press('.')}>.</button></td>
                <td><button class="btn btn-outline-dark w-100" onclick={() => calc('=')}>=</button></td>
                <td><button  class="btn btn-outline-dark w-100" onclick={log10}>log10</button></td>   
                <td><button class="btn btn-outline-dark w-100" onclick={''}>tan</button></td>         
                
            </tr>
        </tbody>
    </table>
    </div>
    
    <style>
       
    
        .text-center {
            
            padding: 20px;
            border-radius: 10px;
            max-width: 400px;
            margin: auto;
            margin-top: 50px;
            box-shadow: 0 0 15px rgba(0,0,0,0.5);
        }
    
        .form-control-lg {
            background-color: #000;
            color: rgb(146, 179, 237);
            border: none;
            text-align: right;
            font-size: 2rem;
        }
    
        
    
        
    
        .btn-outline-primary:hover,
        .btn-outline-dark:hover,
        .btn-outline-danger:hover {
            
            color: #ffffff;
        }
    
        table {
            width: 100%;
        }
    
        button {
            min-height: 50px;
        }
    </style>