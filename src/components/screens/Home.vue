<template>
  <div>
    <div class="vml-header">
      <span class="vml-logo--kcdc">KCDC</span>
      <svg class="vml-logo--vml" data-name="Layer 1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 797.79 258.52"><title>vml-white</title><polygon class="cls-1" points="203.04 0 166.06 0 129.26 36.79 92.47 0 55.48 0 129.26 73.78 203.04 0"/><polygon class="cls-1" points="110.77 203.23 55.49 258.51 92.47 258.51 129.26 221.73 166.06 258.51 203.04 258.51 129.26 184.74 110.77 203.23"/><polygon class="cls-1" points="258.5 203.03 258.5 166.04 221.73 129.26 258.5 92.48 258.5 55.5 184.74 129.26 258.5 203.03"/><polygon class="cls-1" points="0 55.48 0 92.47 36.79 129.26 0 166.05 0 203.04 73.78 129.26 0 55.48"/><polygon class="cls-1" points="129.26 110.76 18.5 0 0 0 0 18.49 110.77 129.26 0 240.03 0 258.51 18.5 258.51 129.26 147.75 240.03 258.51 258.5 258.51 258.5 240.01 147.76 129.26 258.5 18.51 258.5 0 240.03 0 129.26 110.76"/><polygon class="cls-1" points="383.19 168.7 348.43 60.17 309.19 60.17 360.32 207.69 406.06 207.69 457.2 60.17 417.95 60.17 383.19 168.7"/><polygon class="cls-1" points="569.56 110.81 529.52 60.17 495.8 60.17 495.8 207.69 529.52 207.69 529.52 113.53 569.56 163.62 609.6 113.53 609.6 207.69 643.32 207.69 643.32 60.17 609.6 60.17 569.56 110.81"/><polygon class="cls-1" points="727.56 175.23 727.56 60.17 693.85 60.17 693.85 207.69 797.79 207.69 797.79 175.24 727.56 175.23"/></svg>
    </div>

    <transition name="component-slide-fade" mode="out-in">
      <default-view v-if="showDefault"></default-view>
      <error-view v-if="showError" :message="message"></error-view>
      <list-view v-if="showList" :title="title" :items="items"></list-view>
      <single-view v-if="showSingle" :speaker="speaker" :title="title" :items="items"></single-view>
    </transition>
  </div>
</template>

<script>
import '../../../node_modules/signalr/jquery.signalR';
import DefaultView from './Default';
import ErrorView from './Error';
import ListView from './List';
import SingleView from './Single';

const $ = require('jquery');

export default {
  name: 'home',
  components: {
    DefaultView,
    ErrorView,
    ListView,
    SingleView,
  },
  data() {
    return {
      showError: false,
      showSingle: false,
      showList: false,
      showDefault: true,
      message: '',
      title: '',
      type: '',
      items: [],
      speaker: false,
    };
  },
  created() {
    const connection = $.hubConnection('https://kcdcalexaskill.azurewebsites.net');
    const signalrProxy = connection.createHubProxy('KCDCSignalRHub');

    let interval = null;

    const restartInterval = () => {
      clearInterval(interval);

      interval = setInterval(() => {
        this.$data.showError = false;
        this.$data.showSingle = false;
        this.$data.showList = false;
        this.$data.showDefault = true;
      }, 45000);
    };
    restartInterval();
    signalrProxy.on('list', (name, message) => {
      this.$data.showError = false;
      this.$data.showSingle = false;
      this.$data.showList = true;
      this.$data.showDefault = false;
      this.$data.speaker = false;
      this.$data.title = message.title;
      this.$data.items = message.items;
      restartInterval();
    });
    signalrProxy.on('speakerDetail', (name, message) => {
      this.$data.showError = false;
      this.$data.showSingle = true;
      this.$data.showList = false;
      this.$data.showDefault = false;
      this.$data.title = message.title;
      this.$data.items = message.items;
      this.$data.speaker = message.speaker[0];
      restartInterval();
    });
    signalrProxy.on('error', (name, message) => {
      this.$data.showError = true;
      this.$data.showSingle = false;
      this.$data.showList = false;
      this.$data.showDefault = false;
      this.$data.items = false;
      this.$data.speaker = false;
      this.$data.message = message.message;
      restartInterval();
    });
    $.connection.hub.url = '/signalr';
    $.connection.hub.logging = true;
    connection.start({ withCredentials: false });
  },
};
</script>
