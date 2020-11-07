<template>
  <div class="view">
    <div class="user__icon">
        <div class="user__icon_container">
            <img src="../../assets/image.png" alt="first user">
            <img src="../../assets/image1.png" alt="second user">
            <img src="../../assets/image2.png" alt="third user">
            <img src="../../assets/image3.png" alt="fourth user">
            <div class="users">
                <img src="../../assets/image4.png" alt="users">
            </div>
        </div>
        <div class="invite__button">
            <img src="../../assets/image5.png" alt="invite user">
        </div>
    </div>
    <div class="user">
        <img @click="getAlt($event.target.alt)" src="../../assets/image.png" alt="Alma Llogd">
        <img @click="getAlt($event.target.alt)" src="../../assets/image1.png" alt="Marvin Lambert">
        <img @click="getAlt($event.target.alt)" src="../../assets/image2.png" alt="Katie Grane">
        <img @click="getAlt($event.target.alt)" src="../../assets/image3.png" alt="Brian Adam">
        <img @click="getAlt($event.target.alt)" src="../../assets/image6.png" alt="Nora Barnett">
        <img @click="getAlt($event.target.alt)" src="../../assets/image7.png" alt="Adam Malone">
    </div>
    <div class="view__settings">
        <div class="sound">
            <img src="../../assets/v1.png" alt="v1">
        </div>
        <div class="video">
            <img src="../../assets/v2.png" alt="v2">
        </div>
        <div class="full">
            <img src="../../assets/v3.png" alt="v3">
        </div>
        <div class="out">
            <img src="../../assets/v4.png" alt="v4">
            <img src="../../assets/v5.png" alt="v5">
        </div>
        <div class="scale">
            <div class="scale__up">
                <img src="../../assets/+.png" alt="v6">
            </div>
            <div class="scale__value">
                <img src="../../assets/v6.png" alt="v8">
            </div>
            <div class="scale__down">
                <img src="../../assets/-.png" alt="v7">
            </div>
        </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'View',
  date() {
      return {
          alt: ''
      }
  },
  methods: {
      getAlt(elem) {
          this.$emit('alt', elem);
      }
  }
}
</script>

<style>
.view {
    height: 100%;
    width: 55%;
    display: flex;
    flex-direction: column;
}
.user__icon {
    height: 17%;
    width: 100%;
    display: flex;
    flex-direction: row;
    align-items: flex-end;
    justify-content: center;
    margin-bottom: 20px;
}
.user__icon_container {
    height: 80px;
    width: 345px;
    background-color: #ffffff;
    border-radius: 5px;
    display: flex;
    flex-direction: row;
    justify-content: space-evenly;
    align-items: center;
    margin-right: 35px;
    box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.05);
}
.user__icon_container img {
    height: 60px;
    width: 55px;
    cursor: pointer;
}
.users {
    height: 60px;
    width: 55px;
    background-color: #E1E1E2;
    display: flex;
    justify-content: center;
    align-items: center;
}
.users img {
    height: 35px;
    width: 34px;
}
.invite__button {
    height: 60px;
    width: 144px;
    background-color: #ffffff;
    border-radius: 6px;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-bottom: 8px;
    box-shadow: 0px 4px 40px rgba(0, 0, 0, 0.25);
}
.invite__button img {
    cursor: pointer;
}
.user {
    height: 66%;
    width: 100%;
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
}
@media screen and (max-width: 1200px) {
  .user__icon_container {
      width: 300px;
  }
  .invite__button {
    width: 110px;
  }
  .user img {
    height: 30%;
    max-width: 20%;
  }
  .view__settings {
    width: 70%;
  }
}
.user img {
    height: 50%;
    min-width: 33%;
    cursor: pointer;
}
.user img:nth-child(1) {
    border-radius: 20px 0px 0px 0px;
}
.user img:nth-child(4) {
    border-radius: 0px 0px 0px 20px;
}
.user img:nth-child(3) {
    border-radius: 0px 20px 0px 0px;
}
.user img:nth-child(6) {
    border-radius: 0px 0px 20px 0px;
}
.sound, .video, .full {
    height: 60px;
    width: 60px;
    background-color: #ffffff;
    display: flex;
    justify-content: center;
    align-items: center;
    box-shadow: 0px 4px 40px rgba(0, 0, 0, 0.25);
}
.sound img {
    height: 29.29px;
    width: 21.58px;
    cursor: pointer;
}
.video img {
    height: 18.5px;
    width: 27.75px;
    cursor: pointer;
}
.out, .scale img {
    cursor: pointer;
}
.out {
    height: 60px;
    width: 161.54px;
    background-color: #ffffff;
    display: flex;
    justify-content: center;
    align-items: center;
    box-shadow: 0px 4px 40px rgba(0, 0, 0, 0.25);
}
.out img:nth-child(1) {
    margin-right: 8px;
}
.full img {
    height: 36.64px;
    width: 37px;
    cursor: pointer;
}
.scale {
    height: 60px;
    border-radius: 6px;
    width: 161.54px;
    display: flex;
    flex-direction: row;
    box-shadow: 0px 4px 40px rgba(0, 0, 0, 0.25);
}
.scale__up, .scale__down, .scale__value {
    height: 60px;
    width: 46px;
    background-color: #3D42DF;
    display: flex;
    justify-content: center;
    align-items: center;
}
.scale__value {
    height: 60px;
    width: 69.45px;
    background-color: #ffffff;
}
.view__settings {
    height: 17%;
    width: 100%;
    display: flex;
    flex-direction: row;
    justify-content: space-evenly;
    margin-top: 20px;
}
</style>
