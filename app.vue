<template>
  <div class="container">
    <h1>Baby Name Generator</h1>
    <p>Choose your options and click the 'Find names' button below.</p>
    <div class="options-container">
      <div class="option-container">
        <h4>1) Choose a gender</h4>
        <div class="option-buttons">
          <button class="option option-left">Boy</button>
          <button class="option">Unisex</button>
          <button class="option option-right">Girl</button>
        </div>
      </div>
      <div class="option-container">
        <h4>2) Choose the name's populariy</h4>
        <div class="option-buttons">
          <button class="option option-left">Trendy</button>
          <button class="option option-right">Unique</button>
        </div>
      </div>
      <div class="option-container">
        <h4>3) Choose the name's length </h4>
        <div class="option-buttons">
          <button class="option option-left">Long</button>
          <button class="option">All</button>
          <button class="option option-right">Short</button>
        </div>
      </div>
    </div> 
  </div>
</template>

<style scoped>
  h1 {
    font-size: 3rem;
  }
  .container {
    color: rgb(27,60,138);
    font-family: Arial, Helvetica, sans-serif;
    margin: 0 auto;
    max-width: 50rem;
    text-align: center;
  }

  .options-container {
    background-color: rgb(255,238,236);
    border-radius: 2rem;
    margin: 4rem  auto 0 auto;
    padding: 1rem;
    position: relative;
    width: 95%;
  }

  .option-container {
    margin-bottom: 2rem;
  }

  .option {
    background-color: white;
    border: none;
    color: rgb(27,60,138);
    cursor: pointer;
    font-size: 1rem;
    font-weight: 200;
    outline: 0.15rem solid rgb(249,87,89);
    padding: 0.75rem;
    transition: all .3s;
    width: 12rem;
  }

  .option:hover {
    background-color: rgb(249,87,89);
    color: white;
  }

  .option-left {
    border-radius: 1rem 0 0 1rem;
  }

  .option-right {
    border-radius: 0 1rem 1rem 0;
  }

</style>