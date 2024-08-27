<script>
export default{
  data(){
    return {
      colorFondo:"",
      colorTexto: "",
      mostrarTexto: false,
      borde: 0,
      texto: "",
      tipografias: ["serif", "sans-serif", "cursive", "Courier New"],
      tipoLetraSelec:"",
      opacidad: false,
      tamañoLetra: "",
    }
  }
}
</script>

<template>
  <body>
    <div class="container">
      <form>
        <label for="colorfondo">Color de fondo</label>
        <input id="colorfondo" type="text" v-model="colorFondo">
        <br><br>

        <label for="colortexto">Color de texto</label>
        <input id="colortexto" type="text" v-model="colorTexto">
        <br><br>

        <label for="mostrartexto">Mostrar texto</label>
        <input id="mostrartexto" type="checkbox" v-model="mostrarTexto">
        <br><br>
        
        <label for="borde">Borde</label>
        <input id="borde" type="range" v-model="borde">
        <br><br>

        <label for="contenido">Contenido textual</label>
        <textarea id="contenido" v-model="texto"></textarea>
        <br><br>

        <label for="tipografia">Tipografia</label>
        <select id="tipografia" v-model="tipoLetraSelec">
          <option v-for="tipografia in tipografias">{{ tipografia }}</option>
        </select>
        <br><br>

        <label for="opacidad">Opaco</label>
        <input id="opacidad" type="checkbox" v-model="opacidad">
        <br><br>

        <label>Tamaño de letra</label><br>
        <input id="Pequeño" type="radio" name="tamaño" value="10px" v-model="tamañoLetra">
        <label for="Pequeño">Pequeño</label>
        <input id="Mediano" type="radio" name="tamaño" value="25px" v-model="tamañoLetra">
        <label for="Mediano">Mediano</label>
        <input id="Grande" type="radio" name="tamaño" value="40px" v-model="tamañoLetra">
        <label for="Grande">Grande</label>
      </form>
    </div>

    <div id="box-resultado">
      <div id="resultado" :style="{backgroundColor: colorFondo, color: colorTexto, borderRadius: borde + 'px'}"
        :class="{'opacidad': opacidad == true}">

        <p v-show="mostrarTexto" :style="{fontFamily: tipoLetraSelec, fontSize: tamañoLetra}">{{ texto }}</p>

      </div>
    </div>
    
  </body>
</template>

<style scoped>
body {
  display: flex;
  justify-content: center;
}

.container {
  background-color: #3c166efb;
  color: #fff;
  width: 400px;
  padding: 20px;
}

input:not([type="checkbox"], [type="radio"]),textarea,select{
  width: 100%;
  resize: none;
}

#box-resultado{
  width: 400px;
  height: 450px;
  margin-left: 30px;
  display: flex;
  align-items: center;
  justify-content: center;
}

#resultado{
  width: 300px;
  height: 300px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.opacidad{
  opacity: 0.4;
}
</style>
