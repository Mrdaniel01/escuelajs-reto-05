## DESCRIPTION

Solución al reto 05 de Escuela de JavaScript

Nombre: Juan Rios [C5]
Usuario Platzi: JuanDanielRR

## Ciudad
- [ ] Ciudad de México
- [x] Bogotá

## Reto:
  - [x] Primer problema
  
  localStorage.setItem('next_fetch', API)
  
  
  
  - [x] Segundo problema
  
  var APILocal = localStorage.getItem('next_fetch')
  
  async function loadData() {
  await getData(API);
}
  
  - [x] Tercer problema
  
  const $app = document.getElementById('app');
const $observe = document.getElementById('observe');
const API = 'https://rickandmortyapi.com/api/character/';
localStorage.setItem('next_fetch', API)
var APILocal = localStorage.getItem('next_fetch')

const getData = APILocal => {
  fetch(APILocal)
    .then(response => response.json())
    .then(response => {
      const characters = response.results;
      let output = characters.map(character => {
        return `
      <article class="Card">
        <img src="${character.image}" />
        <h2>${character.name}<span>${character.species}</span></h2>
      </article>
    `
      }).join('');
      let newItem = document.createElement('section');
      newItem.classList.add('Items');
      newItem.innerHTML = output;
      $app.appendChild(newItem);
    })
    .catch(error => console.log(error));
}

async function loadData() {
  await getData(API);
}

const intersectionObserver = new IntersectionObserver(entries => {
  if (entries[0].isIntersecting) {
    loadData();
  }
}, {
  rootMargin: '0px 0px 100% 0px',
});


intersectionObserver.observe($observe);
  
  - [ ] Cuarto Problema (Opcional)
