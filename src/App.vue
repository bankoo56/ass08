<template>
  <header>
    <h1 class="text-center">DOG FIGHTER</h1>
  </header>
  <div class="head">
    <button class="btn btn-danger d-grid gap-3 col-2 mx-auto" @click="getDog1(); sum(atk1, atk2);">START</button>
  </div>

  <div style="display: flex;">
    <div style="flex-basis: 50% ; display: flex; justify-content: center;">
      <div class="box" style="background-image:url(https://publicdomainvectors.org/tn_img/Art-Deco-Frame.webp);">
        <h2 class="text-center">Your dog</h2>
        <img :src="dog1.message" alt="">
        <h2 class="text-center">ATK : {{ atk1 }}</h2>
      </div>
    </div>
    <div style="flex-basis: 50% ; display: flex; justify-content: center;">
      <div class="box" style="background-image:url(https://publicdomainvectors.org/tn_img/Art-Deco-Frame.webp);">
        <h2 class="text-center">Enemy</h2>
        <img :src="dog2.message" alt="">
        <h2 class="text-center">ATK : {{ atk2 }}</h2>
      </div>
    </div>
  </div>
  <footer class="text-center">
    <h3>{{ vs }}</h3>
    <br>
    <p>https://dog.ceo/dog-api/documentation/random</p>
  </footer>


</template>
<script>
export default {
  data() {
    return {
      dog1: {},
      dog2: {},
      atk1: 0,
      atk2: 0,
      vs: ""

    }
  },
  methods: {
    getDog1() {
      fetch('https://dog.ceo/api/breeds/image/random')
        .then(res => res.json())
        .then(data => this.dog1 = data)
      this.atk1 = Math.floor(Math.random() * (10 - 1 + 1)) + 1
      fetch('https://dog.ceo/api/breeds/image/random')
        .then(res => res.json())
        .then(data => this.dog2 = data)
      this.atk2 = Math.floor(Math.random() * (10 - 1 + 1)) + 1
    },
    sum(atk1, atk2) {
      if (atk1 > atk2) {
        this.vs = "YOU WIN !!!!"
      } if (atk1 < atk2) {
        this.vs = "YOU LOSE !!!!"
      } if (atk1 == atk2) {
        this.vs = "DRAW !!!!"

      }
    }
  }
}
</script>
<style scoped>
img {
  display: block;
  margin-left: auto;
  margin-right: auto;
  width: 70%;
  height: 70%;
  border-radius: 100%;
  box-shadow: 5px 10px 10px dimgray;
}

.box {
  box-shadow: 1px 1px 30px;
  border-radius: 100%;
  align-items: center;
  opacity: 100%;
  padding: 5vh;
  width: 50%;
  height: 30rem;
  background-repeat: no-repeat;
  background-position: center;
  background-size: contain;

}

h2 {
  color: rgb(255, 255, 255);
  font-size: 40px;
  text-shadow: 5px 3px 10px;
  font-style: oblique;
}

h1 {
  font-size: 50px;
  margin-bottom: -30px;
  margin-top: 5%;
  font-style: italic;

}

.head {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 200px;
  background-repeat: no-repeat;
  background-position: center;
  background-size: contain;
  background-image: url(https://cutewallpaper.org/cdn-cgi/mirage/2af0adefb1b7ebf6af3b94bf8b86378693ec8b55d34af727ac0cbb58dfd044f5/1280/24/scoreboard-png/scoreboard.png);
}

* {
  text-shadow: 2px 2px 10px;
}
</style>