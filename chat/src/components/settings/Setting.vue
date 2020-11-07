<template>
  <div class="setting">
    <div class="setting__container">
        <img src="../../assets/gr.png" alt="gr">
        <img src="../../assets/gr1.png" alt="gr1">
        <img src="../../assets/gr2.png" alt="gr2">
        <img src="../../assets/gr3.png" alt="gr3">
        <img src="../../assets/gr4.png" alt="gr4">
        <img src="../../assets/gr5.png" alt="gr5">
    </div>
  </div>
</template>

<script>

export default {
  name: 'Setting',
}
</script>

<style scoped>
.setting {
    height: 100%;
    width: 15%;
    display: flex;
    justify-content: center;
    align-items: center;
}
.setting__container {
    height: 589px;
    width: 95px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-evenly;
    background-color: #ffffff;
    border-radius: 10px;
    box-shadow: 10px 20px 40px rgba(0, 0, 0, 0.1);
}
.setting__container img {
    cursor: pointer;
}
</style>
