<template>
  <div class="chat">
      <div class="chat__container">
          <div class="icon__block">
          <div class="icon">
              <img class="icon__image" src="../../assets/wi-fi.svg" alt="icon">
              <img class="icon__text" src="../../assets/Live.svg" alt="text">
          </div>
      </div>
      <div class="messages" ref="messages">
          <div ref="messageContainer" class="container">
          <div class="message__user" :class="{'userStyle': item.fromuser === 'Alma Llogd', 'guestStyle': item.fromuser !== 'Alma Llogd'}" v-for="(item, index) in arr" :key="item.id">
              <div class="span">
                <div v-if="arrIcons.includes(index)" :class="{'reverseFlex': item.fromuser !== 'Alma Llogd'}" class="image__user">
                    <span>{{item.fromuser}}</span>
                    <img :src="item.img" alt="user">
                </div>
                <div class="span__container">
                    <span :class="{'spanUser': item.fromuser === 'Alma Llogd', 'spanGuest': item.fromuser !== 'Alma Llogd'}" class="span__messages">{{item.mess}}</span>
                </div>
              </div>
          </div>
          </div>
      </div>
      <div class="enter">
          <div class="inp__container">
              <input type="text" v-model="userMess.mess">
              <div class="enter__button" @click="enterMessage">
                <img src="../../assets/SMS.svg" alt="enter">
              </div>
          </div>
      </div>
      </div>
  </div>
</template>

<script>

export default {
  name: 'Chat',
  updated() {
      this.$refs.messages.scrollTop = this.$refs.messages.scrollHeight;
  },
  created() {
    fetch("http://localhost:3000/message")
    .then(response => response.json())
    .then(data => {this.arr = data});
  },
  data() {
    return {
      userMess: {
          img: 'image.png',
          mess: '',
          fromuser: 'Alma Llogd',
          touser: 'Katie Grane'
      },
      arr: [],
      arrIcons: [0]
    }
  },
  watch: {
      arr(){
        this.arrIcons=[0];
        this.arr.forEach((elem, ind, arr) => {
            if(ind !== arr.length-1) {
                if (arr[ind].fromuser !== arr[ind+1].fromuser) {
                    this.arrIcons.push(ind+1);
                }
            }
        })
          return this;
      }
  },
  methods: {
      enterMessage() {
          if (this.userMess.mess !== '') {
              this.postRequest();
              this.getRequest();
              this.userMess.mess='';
          } else {
              alert('Invalid string length.');
          }
      },
      postRequest() {
          const requestOptions = {
            method: "POST",
            headers: { "Content-Type": "application/json" },
            body: JSON.stringify({
                img: this.userMess.img,
                mess: this.userMess.mess,
                fromuser: this.userMess.fromuser,
                touser: this.userMess.touser
            })
        };
      fetch("http://localhost:3000/message", requestOptions);
      },
      getRequest() {
          fetch("http://localhost:3000/message")
          .then(response => response.json())
        .then(data => {this.arr = data});
      }
  }
}
</script>

<style>
.chat {
    height: 100%;
    width: 30%;
    display: flex;
    justify-content: center;
    align-items: center;
}
.chat__container {
    height: 90%;
    width: 65%;
    background-color: #ffffff;
    border-radius: 20px;
    display: flex;
    flex-direction: column;
}
.messages {
    height: 78vh;
    width: 100%;
    display: grid;
    overflow-y: scroll;
}
.messages::-webkit-scrollbar {
	-webkit-appearance: none;
	width: 7px;
}
.userStyle {
    justify-content: flex-end;
}
.guestStyle {
    justify-content: flex-start;
}
.container {
    width: 100%;
    display: flex;
    align-self: flex-end;
    flex-direction: column;
    justify-content: flex-end;
}
.icon__block {
    height: 10%;
    width: 100%;
    position: relative;
    border-bottom: 1px solid #F4F4F4;
}
.reverseFlex {
    flex-direction: row-reverse;
}
.image__user {
    height: 50px;
    width: 100%;
    display: flex;
    justify-content: flex-end;
    align-items: center;
    font-family: Roboto;
    font-style: normal;
    font-weight: 900;
    font-size: 12px;
    line-height: 14px;
}
.image__user img {
    height: 34.27px;
    width: 29.53px;
    margin-left: 10px;
    margin-right: 8px;
}
.span__container {
    display: flex;
    flex-direction: column;
}
.icon {
    height: 34px;
    width: 130px;
    border-radius: 6px;
    background-color: #3D42DF;
    position: absolute;
    top: 16px;
    left: 19px;
}
.message__user {
    width: 100%;
    display: flex;
    margin-top: 3px;
    margin-bottom: 6px;
}
.span__messages {
     word-break: break-all;
    padding: 10px;
    border-radius: 20px;
}
.span {
    display: flex;
    flex-direction: column;
}
.spanUser {
    margin-right: 3px;
    color: #ffffff;
    background-color: #3D42DF;
    align-self: flex-end;
}
.spanGuest {
    margin-left: 7px;
    background-color: #F3F4F9;
    color: #000000;
    align-self: flex-start;
}
.icon__image {
    height: 20.77px;
    width: 20.77px;
    margin-top: 5px;
    margin-left: 13px;
}
.icon__text {
    margin-bottom: 3px;
    margin-left: 6px;
}
.enter {
    width: 100%;
    height: 74px;
}
.inp__container {
    height: 51px;
    width: 87%;
    position: relative;
}
.enter input {
    height: 100%;
    width: 82%;
    border-radius: 10px;
    border: 1px solid #E1E1E2;
    margin-left: 16px;
    padding-right: 50px;
}
@media screen and (max-width: 1200px) {
    .enter input {
    width: 65%;
  }
}
@media screen and (max-width: 900px) {
    .enter input {
    width: 50%;
  }
  .enter__button {
    right: -18px;
  }
}
.enter__button {
    position: absolute;
    top: 11px;
    right: -8px;
    width: 31px;
    height: 31px;
    border-radius: 5px;
    background-color: #3D42DF;
    display: flex;
    align-items: center;
    justify-content: center;
}
</style>
