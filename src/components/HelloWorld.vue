<template>
  <section class="container letreiro">
    <h1 v-if="!running" data-anima="top">
      <div class="logo">
        <span>•</span>
        <span>•</span>
        <span>•</span>
      </div>
      Letreiro Online
    </h1>
    <div
      :class="{ running: running }"
      class="output"
      :style="`background: ${color.fundo};`"
      data-anima="rigth"
    >
      <h2 :style="`color: ${color.letra};`">
        {{ text }}
      </h2>
    </div>
    <div v-if="!running" data-anima="bottom">
      <input
        style="text-transform: uppercase"
        type="text"
        placeholder="Digite o seu texto"
        v-model="text"
        @keyup="calcSpace"
      />
      <div class="acoes">
        <input
          type="color"
          value="#000000"
          v-model="color.letra"
          @change="neon"
        />
        <input type="color" value="#ffffff" v-model="color.fundo" />
        <button class="btn" @click.prevent="run">Iniciar</button>
      </div>
    </div>
    <div class="stop" @click="stop" v-if="running"></div>
  </section>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      running: false,
      text: "Digite o seu texto",
      color: {
        letra: "#000000",
        fundo: "#ffffff",
      },
    };
  },
  methods: {
    neon() {
      document.documentElement.style.setProperty(
        "--cor_letra",
        this.color.letra
      );
    },
    calcSpace() {
      document.documentElement.style.setProperty(
        "--ate_quando",
        `-${this.text.length * 10}%`
      );
    },
    run() {
      this.running = true;
      document.body.style.background = this.color.fundo;
    },
    stop() {
      if (this.running) {
        this.running = false;
        this.color = {
          letra: "#000000",
          fundo: "#ffffff",
        };
        document.body.style.background = this.color.fundo;
      }
    },
  },
  mounted() {
    document.documentElement.style.setProperty(
      "--ate_quando",
      `-${this.text.length * 10}%`
    );
  },
};
</script>

<style >
:root {
  --ate_quando: -100%;
  --cor_letra: #000;
}
.letreiro {
  margin: 80px auto !important;
  width: 100%;
}
.letreiro h1 {
  font-size: 32px;
  padding-left: 50px;
  display: flex;
  align-items: center;
}
.logo {
  width: 35px;
  height: 35px;
  background: #000;
  margin: 0 auto;
  border-radius: 5px;
  position: absolute;
  left: 0;
  display: flex;
  align-items: center;
  justify-content: center;
}
.logo span {
  font-size: 22px;
}
.logo span:first-child {
  color: red;
}
.logo span:nth-last-child(2) {
  color: green;
}
.logo span:last-child {
  color: blue;
}

.output {
  min-height: 12vh;
  overflow: hidden;

  margin: 30px auto;
}
.output h2 {
  font-size: 80px;
  font-weight: 800;
  text-transform: uppercase;
  letter-spacing: -4px;
  white-space: nowrap;
  animation: marquee 10s linear infinite both;
  filter: drop-shadow(0 0 30px var(--cor_letra));
}
.output.running h2 {
  font-size: 100px;
  margin-top: 100px;
}

@keyframes marquee {
  0% {
    transform: translateX(100%);
  }

  to {
    transform: translateX(var(--ate_quando));
  }
}
.letreiro input[type="color"] {
  width: 60px;
  padding: 7px;
  margin: 0;
  cursor: pointer;
}
.letreiro .btn {
  margin: 0;
}
.letreiro .acoes {
  display: flex;
  align-items: center;
  justify-content: flex-end;
  gap: 20px;
}
.stop {
  width: 100%;
  height: 150vh;
  background: transparent;
  position: absolute;
  top: 0;
  left: 0;
  z-index: 9999;
}
</style>