
<script>
    let display = $state('');

       function clear() {
        display='';
       }
       function calc() {
         display = eval(display);
       }
       function press(c) {
         display+=c;
       }
        </script>





<div class="text-center">
    <input class="form-control-G" readonly bind:value={display} style="font-weight:700;"/>
    <table class="table table-sm table-boderless">
        <tbody>
           <tr>
               <td>
                   <button class="btn btn-dark w-100" 
                           onclick={() => clear('C')} 
                           style="background-image: url('viado.jpg'); background-size: cover; background-position: center; color: white; font-weight: bold; text-shadow: 1px 1px 2px black;">
                       C
                   </button>
               </td>
               <td>
                   <button class="btn btn-dark w-100" 
                           onclick={() => press('(')} 
                           style="background-image: url('imagens/aleatoria2.jpg'); background-size: cover; background-position: center; color: white; font-weight: bold; text-shadow: 1px 1px 2px black;">
                       &lpar;
                   </button>
               </td>
               <td>
                   <button class="btn btn-dark w-100" 
                           onclick={() => press(')')} 
                           style="background-image: url('imagens/aleatoria3.jpg'); background-size: cover; background-position: center; color: white; font-weight: bold; text-shadow: 1px 1px 2px black;">
                       &rpar;
                   </button>
               </td>
               <td>
                   <button class="btn btn-dark w-100" 
                           onclick={() => press('.')} 
                           style="background-image: url('imagens/aleatoria4.jpg'); background-size: cover; background-position: center; color: white; font-weight: bold; text-shadow: 1px 1px 2px black;">
                       /
                   </button>
               </td>
           </tr>
           <tr>
               <td>
                   <button class="btn btn-secondary w-100" 
                           onclick={() => press(7)} 
                           style="background-image: url('imagens/aleatoria5.jpg'); background-size: cover; background-position: center; color: white; font-weight: bold; text-shadow: 1px 1px 2px black;">
                       7
                   </button>
               </td>
               <td>
                   <button class="btn btn-secondary w-100" 
                           onclick={() => press(8)} 
                           style="background-image: url('imagens/aleatoria6.jpg'); background-size: cover; background-position: center; color: white; font-weight: bold; text-shadow: 1px 1px 2px black;">
                       8
                   </button>
               </td>
               <td>
                   <button class="btn btn-secondary w-100" 
                           onclick={() => press(9)} 
                           style="background-image: url('imagens/aleatoria7.jpg'); background-size: cover; background-position: center; color: white; font-weight: bold; text-shadow: 1px 1px 2px black;">
                       9
                   </button>
               </td>
               <td>
                   <button class="btn btn-dark w-100" 
                           onclick={() => press('X')} 
                           style="background-image: url('imagens/aleatoria8.jpg'); background-size: cover; background-position: center; color: white; font-weight: bold; text-shadow: 1px 1px 2px black;">
                       x
                   </button>
               </td>
           </tr>
           <tr>
               <td>
                   <button class="btn btn-secondary w-100" 
                           onclick={() => press(4)} 
                           style="background-image: url('imagens/aleatoria9.jpg'); background-size: cover; background-position: center; color: white; font-weight: bold; text-shadow: 1px 1px 2px black;">
                       4
                   </button>
               </td>
               <td>
                   <button class="btn btn-secondary w-100" 
                           onclick={() => press(5)} 
                           style="background-image: url('imagens/aleatoria10.jpg'); background-size: cover; background-position: center; color: white; font-weight: bold; text-shadow: 1px 1px 2px black;">
                       5
                   </button>
               </td>
               <td>
                   <button class="btn btn-secondary w-100" 
                           onclick={() => press(6)} 
                           style="background-image: url('imagens/aleatoria11.jpg'); background-size: cover; background-position: center; color: white; font-weight: bold; text-shadow: 1px 1px 2px black;">
                       6
                   </button>
               </td>
               <td>
                   <button class="btn btn-dark w-100" 
                           onclick={() => press('-')} 
                           style="background-image: url('imagens/aleatoria12.jpg'); background-size: cover; background-position: center; color: white; font-weight: bold; text-shadow: 1px 1px 2px black;">
                       -
                   </button>
               </td>
           </tr>
           <tr>
               <td>
                   <button class="btn btn-secondary w-100" 
                           onclick={() => press(1)} 
                           style="background-image: url('imagens/aleatoria13.jpg'); background-size: cover; background-position: center; color: white; font-weight: bold; text-shadow: 1px 1px 2px black;">
                       1
                   </button>
               </td>
               <td>
                   <button class="btn btn-secondary w-100" 
                           onclick={() => press(2)} 
                           style="background-image: url('imagens/aleatoria14.jpg'); background-size: cover; background-position: center; color: white; font-weight: bold; text-shadow: 1px 1px 2px black;">
                       2
                   </button>
               </td>
               <td>
                   <button class="btn btn-secondary w-100" 
                           onclick={() => press(3)} 
                           style="background-image: url('imagens/aleatoria15.jpg'); background-size: cover; background-position: center; color: white; font-weight: bold; text-shadow: 1px 1px 2px black;">
                       3
                   </button>
               </td>
               <td rowspan="2" style="height: 0;">
                   <button class="btn btn-dark w-100 h-100" 
                           onclick={() => press('+')} 
                           style="background-image: url('imagens/aleatoria16.jpg'); background-size: cover; background-position: center; color: white; font-weight: bold; text-shadow: 1px 1px 2px black;">
                       +
                   </button>
               </td>
           </tr>
           <tr>
               <td>
                   <button class="btn btn-secondary w-100" 
                           onclick={() => press(0)} 
                           style="background-image: url('imagens/aleatoria17.jpg'); background-size: cover; background-position: center; color: white; font-weight: bold; text-shadow: 1px 1px 2px black;">
                       0
                   </button>
               </td>
               <td>
                   <button class="btn btn-secondary w-100" 
                           onclick={() => press('.')} 
                           style="background-image: url('imagens/aleatoria18.jpg'); background-size: cover; background-position: center; color: white; font-weight: bold; text-shadow: 1px 1px 2px black;">
                       .
                   </button>
               </td>
               <td>
                   <button class="btn btn-dark w-100" 
                           onclick={() => calc('=')} 
                           style="background-image: url('imagens/aleatoria19.jpg'); background-size: cover; background-position: center; color: white; font-weight: bold; text-shadow: 1px 1px 2px black;">
                       =
                   </button>
               </td>
           </tr>
        </tbody>
    </table>
</div>
