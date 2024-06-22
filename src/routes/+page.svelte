<script lang="ts">
  import SquareRoot from "$lib/icons/SquareRoot.svelte";
  import Minus from './../lib/icons/minus.svelte';
  import Division from "$lib/icons/division.svelte";
  import Multiplication from "$lib/icons/multiplication.svelte";
  import Add from "$lib/icons/add.svelte";

function addTOEquation(value : string){
  equation +=value;
}

function backspace(){
  switch (equation.substring(equation.length-3,equation.length)){
case " + ":
case " * ":
case " - ":
case " / ":
equation = equation.substring(0, equation.length -3);
break;
default: 
equation = equation.substring(0, equation.length -1);

  }
}


function clear(){
  equation = "";
}

function solve(){
  equation = eval(equation);
}

function calculateSquareRoot() {
    try {
      const result = Math.sqrt(eval(equation));
      equation = result.toString();
    } catch (error) {
    }
}

  let equation: string =" ";

</script>

<svelte:head>
    <title>
        آلة حاسبة
    </title>
</svelte:head>

<div class="bg-white rounded-3xl font-semibold shadow-2xl
 grid grid-cols-4 gap-1 p-6 max-w-[17rem]" >

 <div class="bg-blue-500 rounded-xl col-span-4 
 min-h-14 flex items-center p-3 mb-2  text-2xl text-white
  font-semibold break-all">
{equation}
</div>
  <button on:click={() => addTOEquation(" /100")} class="  bg-[#f3f6fc] hover:bg-[#f3f6fc]/50 ">%</button>
  <button on:click={() => calculateSquareRoot()} class="   bg-[#f3f6fc]  hover:bg-[#f3f6fc]/50 text-4xl">
    <SquareRoot /> 
  </button>
  <button on:click={()=>backspace()}
    class="   bg-[#f3f6fc]  hover:bg-[#f3f6fc]/50">DEL</button>
  <button on:click={() => clear()} class="  text-white bg-[#1f2b55] hover:bg-[#1f2b55]/90 ">C</button>
  <button on:click={() => addTOEquation("7")}>7</button>
  <button on:click={() => addTOEquation("8")}>8</button>
  <button on:click={() => addTOEquation("9")}>9</button>

  <button on:click={() => addTOEquation(" - ")} class="  text-white bg-[#fc4557] hover:bg-[#fc4557]/90 text-4xl">
<Minus />
  </button>

  <button on:click={() => addTOEquation("4")}>4</button>
  <button on:click={() => addTOEquation("5")}>5</button>
  <button on:click={() => addTOEquation("6")}>6</button>

  <button on:click={() => addTOEquation(" / ")} class="  text-white bg-[#2285fd] hover:bg-[#2285fd]/80 text-3xl">
<Division />
  </button>

  <button on:click={() => addTOEquation("1")}>1</button>
  <button on:click={() => addTOEquation("2")}>2</button>
  <button on:click={() => addTOEquation("3")}>3</button>

  <button on:click={() => addTOEquation(" * ")} class="  text-white bg-[#f9c80e] hover:bg-[#f9c80e]/80 text-3xl">
    <Multiplication />
  </button>

  <button on:click={() => addTOEquation(".")}>.</button>
  <button on:click={() => addTOEquation("0")}>0</button>
  <button on:click={() => solve()} class="  bg-[#f3f6fc]  hover:bg-[#f3f6fc]/50">=</button>
  
  <button on:click={() => addTOEquation(" + ")} class="  text-white bg-[#63dc74]  hover:bg-[#63dc74]/80 text-3xl">
   <Add />
  </button>

</div>
