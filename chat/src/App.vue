<template>
  <div class="main">
    <Setting></Setting>
    <View></View>
    <Chat></Chat>
  </div>
</template>

<script>
import Chat from './components/chat/Chat.vue';
import Setting from './components/settings/Setting.vue';
import View from './components/view/View.vue';

export default {
  name: 'App',
  components: {
    View,
    Chat,
    Setting
  }
}
</script>

<style>
body {
  margin: 0;
}
#app{
  height: 100vh;
  width: 100%;
  background-color: #E5E5E5;
}
.main {
  height: 100%;
  width: 100%;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
}
</style>
