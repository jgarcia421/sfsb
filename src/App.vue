<script setup>
  import { ref } from 'vue'
  import { onMounted } from 'vue'
  
  const password = ref('');
  const validated = ref(false);
  
  function verifyPassword() {
    if(password.value == 'IsItChristmasYet') {
      validated.value = true;
    }
  }
  
  onMounted(() => {
    // Code here runs when the component is mounted
    console.log('Component has been mounted')
  })
</script>

<template>
  
  <div class="password-form" v-if="validated === false">
    <label>Enter Super-Secret Password</label>
    <input type="password" v-model="password" />
    <div>
      <button v-on:click="verifyPassword()">Continue</button>
    </div>
  </div>
  
  <div class="clue" v-if="validated === true">
    <div class="line-1">We knew you could do this and that you'd not fail!</div>
    <div class="line-2">To find the next clue you must go check the mail!</div>
  </div>
  
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

.clue {
  text-align:center;
  font-size:2.5em;
  
  .line-1 {
    color:#53ac18;
  }
  
  .line-2 {
    color:#ac1818;
  }
}

.password-form {
  display:block;
  text-align:center;
  margin:0 auto;
  
  label {
    display:block;
    font-size:3em;
  }
  
  input {
    font-size:2em;
    text-align:center;
    border:none;
    border-bottom:solid 2px #b1e9f3; 
    transition:background-color 250ms, outline 250ms;
    line-height:1em;
    padding:0;
    width:15em;
    margin:0.5em 0;
    
    &:focus {
      outline:none;
      background-color:#fff;
    }
  }
  
  button {
    font-family: "Nunito", sans-serif;
    -webkit-appearance:none;
    background-color:#00d198;
    border:none;
    font-size:1.5em;
    color:#fff;
    border-radius:10px;
    padding:0.5em 1em;
    margin:0.5em 0;
    font-weight:700;
  }
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
