<template>
<div><p class="titulo">piadas do chuck norris</p></div>
  <div class="chuck">
    <p class="text">{{ mensagem }}</p>
    <button @click=" procurar ">Norris</button>
  </div>
</template>

<script>
export default {
  name: "App",
  data(){
    return{
      mensagem:""
    };
  },
  methods:{
    procurar() {
    fetch(`https://api.chucknorris.io/jokes/random`)
    .then(r => r.json())
    .then((r) => {
      this.mensagem = r.value
    })
     .catch(error => {
          console.error(error);
        });
  }
  }
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Kanit:ital,wght@1,200;1,500&display=swap');
*{
  padding:0;
  margin:0;
}
body{
  background-color:#000;
  height:100vh;
  display:flex;
  justify-content:center;
  align-items:center;
}
.text{
  font-family: 'Kanit', sans-serif;
  font-weight:200;
  letter-spacing:2px;
  padding:1rem;
  color:#0f0;
}
.titulo{
    font-size:1.5rem;
  font-weight:500;
  font-family: 'Kanit', sans-serif;
  color:#0f0;
}

button {
  border: none;
  padding: 0.8em 2.5em;
  outline: none;
  margin:1rem;
  color: white;
  font-style: 1.2em;
  position: relative;
  z-index: 1;
  cursor: pointer;
  background: none;
  text-shadow: 3px 3px 10px rgba(0, 0, 0, 0.45);
}

button:before,
button:after {
  position: absolute;
  top: 50%;
  left: 50%;
  border-radius: 10em;
  -webkit-transform: translateX(-50%) translateY(-50%);
  transform: translateX(-50%) translateY(-50%);
  width: 105%;
  height: 105%;
  content: "";
  z-index: -2;
  background-size: 400% 400%;
  background: linear-gradient(
    60deg,
    #00ff00,
    #07b555
  );
}

button:before {
  -webkit-filter: blur(7px);
  filter: blur(7px);
  -webkit-transition: all 0.25s ease;
  transition: all 0.25s ease;
  -webkit-animation: pulse 10s infinite ease;
  animation: pulse 10s infinite ease;
}

button:after {
  -webkit-filter: blur(0.3px);
  filter: blur(0.3px);
}

button:hover:before {
  width: 115%;
  height: 115%;
}
.chuck{
  display:flex;
  flex-direction:column;
  align-items:center;
  justify-content:space-between;
  height:300px;
  width:50vw;
  background-color:#444;
  border-radius:1rem;
  box-shadow: #00ff00 0px 10px 30px -10px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
