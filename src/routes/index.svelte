<script>
  import ProgressBlock from '../lib/ProgressBlock.svelte'
  let countDown = 30
  let sets = []
  let index = 1
  let countDownColor = 'text-green-600'
  let borderColor = 'border-slate-500'
  let buttonState = false
  function handleClick(){
    let tempCount = countDown
    buttonState = true
    setInterval(countIt, 1000)

  }
  function countIt() {
    countDown--
    if(countDown < 6){
      countDownColor = 'text-red-600'
    }
    if((index % 2 == 0) && countDown === 0){
      countDown = 30
      countDownColor = 'text-green-600'
      borderColor = 'border-slate-500'
      index++
    }
    else if(countDown === 0){
      sets = [...sets, index]
      countDown = 30
      countDownColor = 'text-yellow-600'
      borderColor = 'border-yellow-500'
      index++
    }
  }
</script>

<div class="text-center justify-center">
  <h1 class="bg-green-100 p-4 border-b-2 border-slate-500 text-4xl">Interval Timer</h1>
  <h2 class="m-10 text-9xl border-4 {borderColor} rounded-full {countDownColor}">{countDown}</h2>

  <button class="border rounded bg-blue-200 hover:bg-blue-300 p-2 disabled:bg-slate-100" disabled={buttonState} on:click={handleClick}>Start</button>
  <div id="sets" class="grid grid-cols-5 gap-4 m-4">
    {#each sets as set}
       <ProgressBlock/>
    {/each}
  </div>
  

</div>