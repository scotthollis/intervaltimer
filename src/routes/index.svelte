<script>
  let countDown = 30
  let countDownColor = 'text-green-600'
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
    if(countDown === 0){
      countDown = 30
      countDownColor = 'text-green-600'
    }
  }
</script>

<div class="text-center justify-center">
  <h1 class="bg-green-100 p-4">Interval Timer</h1>
  <h2 class="m-10 text-9xl border-4  rounded-full {countDownColor}">{countDown}</h2>

  <button class="border rounded bg-blue-200 hover:bg-blue-300 p-2 disabled:bg-slate-100" disabled={buttonState} on:click={handleClick}>Start</button>
  <div></div>
  

</div>