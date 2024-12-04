<template>
  <div id="app">
    <div class="controls">
      <div>
        <label>Color de fondo</label>
        <input v-model="backgroundColor" type="text" />
      </div>
      <div>
        <label>Color de texto</label>
        <input v-model="textColor" type="text" />
      </div>
      <div>
        <label>Mostrar texto</label>
        <input v-model="showText" type="checkbox" />
      </div>
      <div>
        <label>Borde</label>
        <input v-model="borderRadius" type="range" min="0" max="50" />
      </div>
      <div>
        <label>Contenido textual</label>
        <textarea v-model="textContent"></textarea>
      </div>
      <div>
        <label>Tipografía</label>
        <select v-model="fontFamily">
          <option v-for="font in fonts" :key="font" :value="font">{{ font }}</option>
        </select>
      </div>
      <div>
        <label>Opaco</label>
        <input v-model="isOpaque" type="checkbox" />
      </div>
      <div>
        <label>Tamaño de letra</label>
        <input v-model="fontSize" type="radio" value="small" /> Pequeño
        <input v-model="fontSize" type="radio" value="medium" /> Mediano
        <input v-model="fontSize" type="radio" value="large" /> Grande
      </div>
    </div>
    <div class="preview" :style="previewStyles">
      <span v-show="showText">{{ textContent }}</span>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      backgroundColor: 'green',
      textColor: 'white',
      showText: true,
      borderRadius: 25,
      textContent: 'Awesome Vue.js',
      fontFamily: 'sans-serif',
      isOpaque: false,
      fontSize: 'medium',
      fonts: ['sans-serif', 'serif', 'cursive', 'monospace']
    };
  },
  computed: {
    previewStyles() {
      return {
        backgroundColor: this.backgroundColor,
        color: this.textColor,
        borderRadius: this.borderRadius + 'px',
        fontFamily: this.fontFamily,
        opacity: this.isOpaque ? 0.5 : 1,
        fontSize: this.fontSize === 'small' ? '12px' : this.fontSize === 'medium' ? '16px' : '20px',
        display: 'flex',
        alignItems: 'center',
        justifyContent: 'center',
        textAlign: 'center',
        height: '200px',
        width: '200px',
        padding: '20px'
      };
    }
  }
};
</script>

<style scoped>
#app {
  display: flex;
  gap: 20px;
  padding: 20px;
}

.controls {
  display: flex;
  flex-direction: column;
  gap: 10px;
  background-color: #2f4f4f;
  color: white;
  padding: 20px;
  border-radius: 8px;
}

.controls input[type="text"],
.controls textarea {
  width: 100%;
  padding: 8px;
  border: none;
  border-radius: 4px;
}

.preview {
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
