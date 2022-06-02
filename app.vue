<template>
  <div class="container">
    <h1>Baby Name Generator</h1>
    <p>Choose your options and click the 'Find names' button below.</p>
    <div class="options-container">
      <div class="option-container">
        <h4>1) Choose a gender</h4>
        <div class="option-buttons">
          <button 
            class="option option-left"
            :class="options.gender === Gender.BOY && 'option-active'"
            @click="updateGender(Gender.BOY)"
          >
            Boy
          </button>
          <button 
            class="option"
            :class="options.gender === Gender.UNISEX && 'option-active'"
            @click="updateGender(Gender.UNISEX)"
          >
            Unisex
          </button>
          <button 
            class="option option-right"
            :class="options.gender === Gender.GIRL && 'option-active'"
            @click="updateGender(Gender.GIRL)"
          >
            Girl
          </button>
        </div>
      </div>
      <div class="option-container">
        <h4>2) Choose the name's populariy</h4>
        <div class="option-buttons">
          <button 
            class="option option-left"
            :class="options.popularity === Popularity.TRENDY && 'option-active'"
            @click="updatePopularity(Popularity.TRENDY)"
          >
            Trendy
          </button>
          <button 
            class="option option-right"
            :class="options.popularity === Popularity.UNIQUE && 'option-active'"
            @click="updatePopularity(Popularity.UNIQUE)"
          >
            Unique
          </button>
        </div>
      </div>
      <div class="option-container">
        <h4>3) Choose the name's length </h4>
        <div class="option-buttons">
          <button 
            class="option option-left"
            :class="options.length === Length.LONG && 'option-active'"
            @click="updateLength(Length.LONG)"
          >
            Long
          </button>
          <button 
            class="option"
            :class="options.length === Length.ALL && 'option-active'"
            @click="updateLength(Length.ALL)"
          >
            All
          </button>
          <button
            class="option option-right"
            :class="options.length === Length.SHORT && 'option-active'"
            @click="updateLength(Length.SHORT)"
          >
            Short
          </button>
        </div>
      </div>
      <button class="primary" @click="computedNames">Find names</button>
    </div> 
    <div class="cards-container">
      <div v-for="name in selectedNames" :key="name" class="card">
        <h3>{{ name }}</h3>
        <p>X</p>
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { Gender, Popularity, Length, names } from '@/data'

  // options interface
  interface Options {
    gender: Gender
    popularity: Popularity
    length: Length
  }

  // state
  const options = reactive(<Options>{
    gender: Gender.GIRL,
    popularity: Popularity.TRENDY,
    length: Length.ALL
  })

  const selectedNames = ref(<string[]>[])

  // methods
  const updateGender = (gender: Gender): Gender => options.gender = gender
  const updatePopularity = (popularity: Popularity) => options.popularity = popularity
  const updateLength = (length: Length) => options.length = length
  const computedNames = (): void => {
    const filteredNames = names
      .filter((name) => name.gender === options.gender)
      .filter((name) => name.popularity === options.popularity)
      .filter((name) => {
        if(options.length === Length.ALL) return true
        else return name.length === options.length
      })

    selectedNames.value = filteredNames.map(name => name.name)
  }
</script>

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

  .option-active {
    background-color: rgb(249,87,89);
    color: white
  }

  .option-left {
    border-radius: 1rem 0 0 1rem;
  }

  .option-right {
    border-radius: 0 1rem 1rem 0;
  }

  .primary {
    background-color: rgb(249,87,89);
    border: none;
    border-radius: 1rem;
    color: white;
    cursor: pointer;
    font-size: 1rem;
    font-weight: 200;
    outline: 0.15rem solid rgb(249,87,89);
    padding: 0.75rem;
    transition: all .3s;
    width: 12rem;
  }

  .primary:hover {
    background: white;
    color: rgb(27,60,138);
  }

  .cards-container {
    display: flex;
    flex-wrap: wrap;
    margin-top: 3rem;
  }

  .card {
    background-color: rgb(27,60,138);
    border-radius: 1rem;
    color: white;
    margin-bottom: 1rem;
    margin-right: 0.5rem;
    padding: 1rem;
    position: relative;
    width: 28%;
  }

  .card p {
    color: rgba(255,255,255,0.178);
    cursor: pointer;
    right: 1rem;
    position: absolute;
    top: 0;
  }

</style>
