<template>
  <div id="app" class="container">
    <div class="card">
      <h1 class="title" :style="titleStyle">Hallo Saya IPANT!</h1>
      <input type="text" v-model="inputText" placeholder="Masukkan teks di sini" />
      <p class="dynamic-text" :class="dynamicClass" :style="dynamicStyle">
        Ini adalah teks yang baru anda masukan: {{ inputText }}
      </p>
      <button @click="changeColor">Disini Ubah Warnanya</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      inputText: '',
      colorIndex: 0,
      colors: ['red', 'blue', 'green', 'purple', 'orange', 'pink']
    };
  },
  computed: {
    dynamicClass() {
      return this.colors[this.colorIndex] + '-text';
    },
    dynamicStyle() {
      return {
        fontSize: '20px',
        fontWeight: 'bold',
        color: this.colors[this.colorIndex]
      };
    },
    titleStyle() {
      return {
        textAlign: 'center',
        marginBottom: '20px'
      };
    }
  },
  methods: {
    changeColor() {
      this.colorIndex = (this.colorIndex + 1) % this.colors.length;
    }
  }
};
</script>

<style>
body {
  background-color: #0d0d0d;
  color: #00ffcc;
  font-family: 'Courier New', Courier, monospace;
  margin: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.container {
  display: flex;
  justify-content: center;
  align-items: center;
  perspective: 1000px;
}

.card {
  background: linear-gradient(145deg, #1a1a1a, #2b2b2b);
  border-radius: 15px;
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.5);
  padding: 40px;
  text-align: center;
  transform: rotateY(15deg);
  transition: transform 0.5s;
}

.card:hover {
  transform: rotateY(0deg) scale(1.05);
}

.title {
  font-size: 30px;
  margin-bottom: 20px;
  color: #ff0099;
}

input {
  display: block;
  width: 100%;
  margin-bottom: 20px;
  padding: 10px;
  font-size: 16px;
  border: none;
  border-radius: 5px;
  background-color: #1a1a1a;
  color: #00ffcc;
  box-shadow: inset 0 0 5px rgba(0, 0, 0, 0.5);
}

input::placeholder {
  color: #555;
}

button {
  padding: 10px 20px;
  font-size: 16px;
  color: #0d0d0d;
  background-color: #00ffcc;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  box-shadow: 0 5px 10px rgba(0, 255, 204, 0.3);
  transition: background-color 0.3s, transform 0.3s;
}

button:hover {
  background-color: #00cca3;
  transform: translateY(-3px);
}

button:active {
  background-color: #009977;
  transform: translateY(1px);
}

.red-text {
  color: red;
}

.blue-text {
  color: blue;
}

.green-text {
  color: green;
}

.purple-text {
  color: purple;
}

.orange-text {
  color: orange;
}

.pink-text {
  color: pink;
}

.dynamic-text {
  font-size: 20px;
  font-weight: bold;
  margin-bottom: 20px;
}
</style>
