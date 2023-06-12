<script setup>
import { ref, onMounted } from 'vue'

const links = ref([])

function loadLinks() {
  const savedLinks = localStorage.getItem('links')
  if (savedLinks) {
    links.value = JSON.parse(savedLinks)
  }
}

function saveLinks() {
  localStorage.setItem('links', JSON.stringify(links.value))
}

onMounted(() => {
  loadLinks()
})

async function Cut() {
  const url = document.getElementById("inputUrl").value
  if (!url) {
    alert("Insira uma URL válida.")
    return
  }

  const headers = {
    "Content-Type": "application/json",
    apiKey: "b001706cbc644268a109321c155cc101"
  }

  const linkRequest = {
    destination: url,
    domain: { fullName: "rebrand.ly" }
  }

  try {
    const response = await fetch("https://api.rebrandly.com/v1/links", {
      method: "POST",
      headers: headers,
      body: JSON.stringify(linkRequest)
    })
    const json = await response.json()

    let inputUrl = document.getElementById("inputUrl")
    inputUrl.value = json.shortUrl

    links.value.push(json.shortUrl)
    saveLinks()
  } catch (error) {
    console.log(error)
  }
}

function Copy() {
  const inputUrl = document.getElementById("inputUrl")
  inputUrl.select()
  inputUrl.setSelectionRange(0, 99999)
    
  navigator.clipboard.writeText(inputUrl.value)
  alert("Copiado para a área de transferência.")
}

function deleteLink(index) {
  links.value.splice(index, 1)
  saveLinks()
}
</script>

<template>
  <nav className="userNav">
    <img src="../assets/link.svg" alt="linkLogo">
    <RouterLink to="/">Exist</RouterLink>
  </nav>
  <div className="UserContainer">
    <h1>Reduza sua URL e compartilhe mais com menos!</h1>
    <div className="boxInput">
      <input className="url" id="inputUrl" type="text" placeholder="Coloque sua URL">
      <button v-on:click="Cut">Encurtar</button>
      <button v-on:click="Copy">Copiar</button>
    </div>

    <ul>
      <li v-for="(link, index) in links" :key="index">
        <span>{{ link }}</span>
        <button className="trash" @click="deleteLink(index)">Excluir</button>
      </li>
    </ul>
  </div>
</template>

<style>
  .userNav a {
    background-color: var(--red-500);
  }
  .userNav a:hover {
    background: var(--red-700);
    transition: background-color 0.2s;
  }
  .UserContainer {
    max-width: 74rem;
    min-height: calc(100vh - 10rem);
    margin: 3rem auto;

    background: var(--gray-800);
    border-radius: 0.5rem;

    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
  }
  h1 {
    font-size: 1.875rem;
    margin-bottom: 1.875rem;
  }
  .boxInput {
    width: 100%;
    display: flex;
    justify-content: center;
    margin-bottom: 2.188rem;
  }
  .url {
    padding: 0.75rem 1.25rem;
    text-align: center;
    outline: transparent;
    width: 40%;
    border-radius: 0.938rem;
    font-size: 1.25rem;
    color: var(--gray-800);
    border: none
  }
  button {
    padding: 0.938rem 1.25rem;
    width: 10rem;
    margin-left: 0.625rem;
    border-radius: 0.938rem;
    background-color: var(--green-500);
    color: var(--white);
    font-size: 1.25rem;
    border: none;
    cursor: pointer;
  }
  button:hover {
    background-color: var(--green-700);
    transition: background-color 0.2s;
  }
  .trash {
    padding: 0.938rem 1.25rem;
    width: 7.5rem;
    margin-left: 0.625rem;
    border-radius: 0.938rem;
    background-color: var(--red-500);
    color: var(--white);
    font-size: 1.25rem;
    border: none;
    cursor: pointer;
  }
  .trash:hover {
    background-color: var(--red-700);
    transition: background-color 0.2s;
  }
  ul {
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  li {
    width: 80%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0.938rem 1.25rem;
    margin-bottom: 0.625rem;
    border-radius: 0.938rem;
    background-color: var(--gray-700);
    color: var(--white);
    font-size: 1.25rem;
  }

</style>

