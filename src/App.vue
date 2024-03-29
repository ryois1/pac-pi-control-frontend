<template>
  <div id="app">
    <main>
      <heartbeat></heartbeat>
      <div
        v-on:click="showInfo()"
        id="status_icon"
        v-bind:class="{ online: ONLINE, offline: !ONLINE }"
        class="text-white text-center"
      >
        <b-icon
          v-if="ONLINE"
          icon="check"
          style="width: 40px; height: 40px"
        ></b-icon>
        <b-icon
          v-else
          icon="exclamation-triangle"
          style="width: 30px; height: 30px"
        ></b-icon>
      </div>
      <router-view></router-view>
    </main>
  </div>
</template>

<script>
import heartbeat from "./components/global/heartbeat.vue";
export default {
  name: "App",
  components: {
    heartbeat,
  },
  data: function () {
    return {
      ONLINE: true,
      API_BASE_URL:
        process.env.NODE_ENV === "development"
          ? "http://localhost:3000/api"
          : "https://api.pac-control.jchsprojects.com/api",
      POWER_STATUS: null,
      MODE_STATUS: null,
      DISPLAY_IP: null,
      X32_IP: null,
    };
  },
  methods: {
    async showInfo() {
      const vm = this;
      vm.$swal.fire({
        title: `System Information`,
        confirmButtonText: 'Close',
        html: `<code>Status: ${vm.ONLINE ? "Online" : "Offline"}<br>API Endpoint: ${vm.API_BASE_URL}<br>Display IP: ${vm.DISPLAY_IP}<br>X32 IP: ${vm.X32_IP}</code>`,
        footer:
          "Developed by Russell Payne 2021. Exclusively for Jefferson County High School.<br><b>NO SUPPORT IS INCLUDED</b>",
      });
    },
  },
};
</script>
<style>
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  height: 100vh;
  -webkit-touch-callout: none;
  -webkit-user-select: none;
  -khtml-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}
#genericbg {
  height: 100vh;
  background-image: url("/assets/backgrounds/BackgroundScaled.png");
  background-size: cover;
  background-repeat: no-repeat;
  background-attachment: fixed;
}
#welcomebg {
  height: 100vh;
  background-image: url("/assets/backgrounds/WelcomeScaled.png");
  background-size: cover;
  background-repeat: no-repeat;
  background-attachment: fixed;
}
#sleepingbg {
  height: 100vh;
  background-image: url("/assets/backgrounds/SleepScreen.png");
  background-size: cover;
  background-repeat: no-repeat;
  background-attachment: fixed;
}
html,
body {
  overflow: hidden;
  height: 100vh;
}
/*Start flashing button for mute*/
.btn-danger.active {
  -webkit-animation: glowing 1500ms infinite;
  -moz-animation: glowing 1500ms infinite;
  -o-animation: glowing 1500ms infinite;
  animation: glowing 1500ms infinite;
}
@-webkit-keyframes glowing {
  0% {
    background-color: #b20000;
    -webkit-box-shadow: 0 0 3px #b20000;
  }
  50% {
    background-color: #ff0000;
    -webkit-box-shadow: 0 0 40px #ff0000;
  }
  100% {
    background-color: #b20000;
    -webkit-box-shadow: 0 0 3px #b20000;
  }
}

@-moz-keyframes glowing {
  0% {
    background-color: #b20000;
    -moz-box-shadow: 0 0 3px #b20000;
  }
  50% {
    background-color: #ff0000;
    -moz-box-shadow: 0 0 40px #ff0000;
  }
  100% {
    background-color: #b20000;
    -moz-box-shadow: 0 0 3px #b20000;
  }
}

@-o-keyframes glowing {
  0% {
    background-color: #b20000;
    box-shadow: 0 0 3px #b20000;
  }
  50% {
    background-color: #ff0000;
    box-shadow: 0 0 40px #ff0000;
  }
  100% {
    background-color: #b20000;
    box-shadow: 0 0 3px #b20000;
  }
}

@keyframes glowing {
  0% {
    background-color: #b20000;
    box-shadow: 0 0 3px #b20000;
  }
  50% {
    background-color: #ff0000;
    box-shadow: 0 0 40px #ff0000;
  }
  100% {
    background-color: #b20000;
    box-shadow: 0 0 3px #b20000;
  }
}
/*End flashing*/
/*Start Spinner*/
.lds-spinner {
  color: official;
  display: inline-block;
  position: relative;
  width: 80px;
  height: 80px;
}
.lds-spinner div {
  transform-origin: 40px 40px;
  animation: lds-spinner 1.2s linear infinite;
}
.lds-spinner div:after {
  content: " ";
  display: block;
  position: absolute;
  top: 3px;
  left: 37px;
  width: 6px;
  height: 18px;
  border-radius: 20%;
  background: #fff;
}
.lds-spinner div:nth-child(1) {
  transform: rotate(0deg);
  animation-delay: -1.1s;
}
.lds-spinner div:nth-child(2) {
  transform: rotate(30deg);
  animation-delay: -1s;
}
.lds-spinner div:nth-child(3) {
  transform: rotate(60deg);
  animation-delay: -0.9s;
}
.lds-spinner div:nth-child(4) {
  transform: rotate(90deg);
  animation-delay: -0.8s;
}
.lds-spinner div:nth-child(5) {
  transform: rotate(120deg);
  animation-delay: -0.7s;
}
.lds-spinner div:nth-child(6) {
  transform: rotate(150deg);
  animation-delay: -0.6s;
}
.lds-spinner div:nth-child(7) {
  transform: rotate(180deg);
  animation-delay: -0.5s;
}
.lds-spinner div:nth-child(8) {
  transform: rotate(210deg);
  animation-delay: -0.4s;
}
.lds-spinner div:nth-child(9) {
  transform: rotate(240deg);
  animation-delay: -0.3s;
}
.lds-spinner div:nth-child(10) {
  transform: rotate(270deg);
  animation-delay: -0.2s;
}
.lds-spinner div:nth-child(11) {
  transform: rotate(300deg);
  animation-delay: -0.1s;
}
.lds-spinner div:nth-child(12) {
  transform: rotate(330deg);
  animation-delay: 0s;
}
@keyframes lds-spinner {
  0% {
    opacity: 1;
  }
  100% {
    opacity: 0;
  }
}
/*End Spinner*/
/*Beign power button*/
#power_button {
  position: absolute;
  border-radius: 25px;
  right: 10px;
  bottom: 10px;
  background-color: #dc3545;
  height: 120px;
  width: 120px;
  transition: color 0.15s ease-in-out, background-color 0.15s ease-in-out,
    border-color 0.15s ease-in-out, box-shadow 0.15s ease-in-out;
}
.power_button_icon {
  background-image: url("/assets/icons/power_button.png");
  height: 120px;
  width: 120px;
  background-size: 120px 120px;
}
#power_button:hover {
  background-color: #b7202e;
}
/*End power button*/
/*Begin online status*/
#status_icon {
  position: absolute;
  border-radius: 25px;
  left: 10px;
  bottom: 10px;
  height: 40px;
  width: 40px;
}
.online {
  background-color: #008000;
}
.offline {
  background-color: #b7202e;
}
/*End online status*/
</style>
