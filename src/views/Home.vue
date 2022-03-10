<template>
  <!-- eslint-disable -->
  <div class="home">
    <transition name="slide-fade" mode="ease-out">
      <PlanetModal
        v-if="modalOpen"
        @close="closeModal"
        :planetName="modalObject.planetName"
        :videoLink="modalObject.videoLink"
        :wikipedia="modalObject.wikipedia"
      />
    </transition>
    <ul class="solarsystem">
      <li v-for="(item, index) in solarSystem" :key="item.index" :class="item.planetClass">
        <a @click="clickPlanet(index)" :href="item.planetLink"
          ><span>{{ item.planetName }}</span></a
        >
      </li>
    </ul>
    <audio class="audio" src="../assets/sounds/transition.mp3"></audio>
    <audio class="music" src="../assets/sounds/music.mp3"></audio>
  </div>
</template>

<script>
import PlanetModal from '../components/PlanetModal.vue';
export default {
  name: 'Home',
  components: {
    PlanetModal,
  },
  data() {
    return {
      modalOpen: false,
      modalObject: {
        videoLink: '',
        planetName: '',
        wikipedia: '',
      },
      solarSystem: [
        {
          planetName: 'Sol',
          planetClass: 'sun',
          planetLink: '#sun',
          planetVideoLink: 'https://www.youtube.com/embed/ZEiJLhtkfGM',
          wikipedia: 'https://pt.wikipedia.org/wiki/Sol',
        },
        {
          planetName: 'Mercúrio',
          planetClass: 'mercury',
          planetLink: '#mercury',
          planetVideoLink: 'https://www.youtube.com/embed/huGvInnMwIY',
          wikipedia: 'https://pt.wikipedia.org/wiki/Merc%C3%BArio_(planeta)',
        },
        {
          planetName: 'Vênus',
          planetClass: 'venus',
          planetLink: '#venus',
          planetVideoLink: 'https://www.youtube.com/embed/M11f_041080',
          wikipedia: 'https://pt.wikipedia.org/wiki/V%C3%A9nus_(planeta)',
        },
        {
          planetName: 'Terra',
          planetClass: 'earth',
          planetLink: '#earth',
          planetVideoLink: 'https://www.youtube.com/embed/cnMWTVsQV-k',
          wikipedia: 'https://pt.wikipedia.org/wiki/Terra',
        },
        {
          planetName: 'Marte',
          planetClass: 'mars',
          planetLink: '#mars',
          planetVideoLink: 'https://www.youtube.com/embed/JsjkzTIByks',
          wikipedia: 'https://pt.wikipedia.org/wiki/Marte_(planeta)',
        },
        {
          planetName: 'Asteroids & Meteorids',
          planetClass: 'asteroids_meteorids',
        },
        {
          planetName: 'Júpiter',
          planetClass: 'jupiter',
          planetLink: '#jupiter',
          planetVideoLink: 'https://www.youtube.com/embed/sJMhnBZLEaE',
          wikipedia: 'https://pt.wikipedia.org/wiki/J%C3%BApiter_(planeta)',
        },
        {
          planetName: 'Saturno',
          planetClass: 'saturn',
          planetLink: '#saturn',
          planetVideoLink: 'https://www.youtube.com/embed/GY4j6R6Mv2s',
          wikipedia: 'https://pt.wikipedia.org/wiki/Saturno_(planeta)',
        },
        {
          planetName: 'Urano',
          planetClass: 'uranus',
          planetLink: '#uranus',
          planetVideoLink: 'https://www.youtube.com/embed/qV8NueymSfQ',
          wikipedia: 'https://pt.wikipedia.org/wiki/Urano_(planeta)',
        },
        {
          planetName: 'Netuno',
          planetClass: 'neptune',
          planetLink: '#neptune',
          planetVideoLink: 'https://www.youtube.com/embed/R1o1GIOZZYk',
          wikipedia: 'https://pt.wikipedia.org/wiki/Netuno_(planeta)',
        },
        {
          planetName: 'Plutão',
          planetClass: 'pluto',
          planetLink: '#pluto',
          planetVideoLink: 'https://www.youtube.com/embed/uPPcONlfU9o',
          wikipedia: 'https://pt.wikipedia.org/wiki/Plut%C3%A3o',
        },
      ],
    };
  },
  mounted() {
    console.log('fui montado');
    this.playMusic(true);
  },
  methods: {
    playTransition() {
      var modalTransitionSound = document.querySelector('.audio');

      return modalTransitionSound.play();
    },
    playMusic(condition) {
      var music = document.querySelector('.music');

      condition ? music.play() : music.pause();
    },
    clickPlanet(index) {
      this.playTransition();
      this.modalObject.videoLink = this.solarSystem[index].planetVideoLink;
      this.modalObject.planetName = this.solarSystem[index].planetName;
      this.modalObject.wikipedia = this.solarSystem[index].wikipedia;
      this.modalOpen = true;
      this.playMusic(false);

    },
    closeModal() {
      this.playTransition();
      this.modalOpen = false;
      this.playMusic(true);
    },
  },
};
</script>
<style lang="scss">
/* Solar System Styles */
ul.solarsystem {
  position: relative;
  min-height: 100vh;
  list-style: none;
  transition: all 0.09s ease-in;
  overflow: hidden;
  padding: 0;
  margin: 0;
  margin-left: 15%;
}
ul.solarsystem li {
  text-indent: -9999px;
  display: block;
  position: absolute;
  border: 2px solid rgba(#394057, 0.75);
}
ul.solarsystem li span {
  display: block;
  position: absolute;
  width: 20px;
  height: 20px;
  border-radius: 999px;
  transition: 0.3s all $transition-function-elastic;
}
ul.solarsystem li a {
  &:hover {
    transform: scale(1.5);
  }
}
ul.solarsystem li.sun {
  width: 40px;
  height: 40px;
  -webkit-border-radius: 20px;
  -moz-border-radius: 20px;
  border-radius: 20px;
  background: #fc3;
  background-image: -webkit-gradient(
    linear,
    left bottom,
    left top,
    color-stop(0.22, rgb(204, 153, 0)),
    color-stop(1, rgb(255, 219, 112))
  );
  background-image: -moz-linear-gradient(
    center bottom,
    rgb(204, 153, 0) 22%,
    rgb(255, 219, 112) 100%
  );
  top: 302px;
  left: 462px;
  border: none;
  -webkit-box-shadow: 0 0 50px #c90;
  -moz-box-shadow: 0 0 50px #c90;
  box-shadow: 0 0 50px #c90;
  z-index: 100;
  -webkit-transition: all 0.2s ease-in;
  -moz-transition: all 0.2s ease-in;
  -o-transition: all 0.2s ease-in;
  transition: all 0.2s ease-in;
  &:hover {
    transform: scale(1.5);
  }
}
ul.solarsystem li.sun span {
  width: 60px;
  height: 60px;
  -webkit-border-radius: 30px;
  -moz-border-radius: 30px;
  border-radius: 30px;
}
ul.solarsystem li.mercury {
  width: 100px;
  height: 100px;
  -webkit-border-radius: 52px;
  -moz-border-radius: 52px;
  border-radius: 52px;
  top: 270px;
  left: 430px;
  z-index: 99;
}
ul.solarsystem li.mercury span {
  background: #b6bac5;
  top: 0px;
  left: 10px;
}
ul.solarsystem li.venus {
  width: 160px;
  height: 160px;
  -webkit-border-radius: 82px;
  -moz-border-radius: 82px;
  border-radius: 82px;
  top: 240px;
  left: 400px;
  z-index: 98;
}
ul.solarsystem li.venus span {
  background: #bf8639;
  top: 118px;
  left: 5px;
}
ul.solarsystem li.earth {
  width: 220px;
  height: 220px;
  -webkit-border-radius: 112px;
  -moz-border-radius: 112px;
  border-radius: 112px;
  top: 210px;
  left: 370px;
  z-index: 97;
}
ul.solarsystem li.earth span {
  background: #06c;
  top: 45px;
  left: 5px;

  &::before {
    content: "";
    width: 4px;
    height: 4px;
    -webkit-border-radius: 2px;
    -moz-border-radius: 2px;
    border-radius: 2px;
    background: #ccc;
    top: 100%;
    left: 100%;
    position: absolute;
  }
}

ul.solarsystem li.mars {
  width: 280px;
  height: 280px;
  -webkit-border-radius: 142px;
  -moz-border-radius: 142px;
  border-radius: 142px;
  top: 180px;
  left: 340px;
  z-index: 96;
}
ul.solarsystem li.mars span {
  background: #aa4200;
  top: 0px;
  left: 175px;
}
ul.solarsystem li.asteroids_meteorids {
  top: 155px;
  left: 315px;
  z-index: 1;
  background: url(http://neography.com/experiment/circles/solarsystem/asteroids_meteorids.png)
    no-repeat 0 0;
  width: 330px;
  height: 330px;
  -webkit-border-radius: 165px;
  -moz-border-radius: 165px;
  border-radius: 165px;
  border: none;
}
ul.solarsystem li.jupiter {
  width: 340px;
  height: 340px;
  -webkit-border-radius: 172px;
  -moz-border-radius: 172px;
  border-radius: 172px;
  top: 150px;
  left: 310px;
  z-index: 95;
}
ul.solarsystem li.jupiter span {
  background: #e0ae6f;
  top: 57px;
  left: 24px;
}
ul.solarsystem li.saturn {
  width: 400px;
  height: 400px;
  -webkit-border-radius: 202px;
  -moz-border-radius: 202px;
  border-radius: 202px;
  top: 120px;
  left: 280px;
  z-index: 94;
}
ul.solarsystem li.saturn span {
  background: #dfd3a9;
  top: 24px;
  left: 300px;

  &::before {
    position: absolute;
    content: "";
    width: 180%;
    height: 180%;
    border-radius: 999px;
    background: transparent;
    border: 3px solid #5a4e34;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%) skew(45deg);
    z-index: -1;
  }
  &::after {
    position: absolute;
    content: "";
    width: 170%;
    height: 170%;
    border-radius: 999px;
    background: transparent;
    border: 2px solid rgb(51, 41, 19);
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%) skew(45deg);
    z-index: -1;
  }
}

ul.solarsystem li.uranus {
  width: 460px;
  height: 460px;
  -webkit-border-radius: 232px;
  -moz-border-radius: 232px;
  border-radius: 232px;
  top: 90px;
  left: 250px;
  z-index: 93;
}
ul.solarsystem li.uranus span {
  background: #82b3d1;
  top: 7px;
  left: 300px;
}
ul.solarsystem li.neptune {
  width: 520px;
  height: 520px;
  -webkit-border-radius: 262px;
  -moz-border-radius: 262px;
  border-radius: 262px;
  top: 60px;
  left: 220px;
  z-index: 92;
}
ul.solarsystem li.neptune span {
  background: #77c2ec;
  top: -5px;
  left: 200px;
}
ul.solarsystem li.pluto {
  width: 580px;
  height: 580px;
  -webkit-border-radius: 292px;
  -moz-border-radius: 292px;
  border-radius: 292px;
  top: 30px;
  left: 190px;
  z-index: 91;
}
ul.solarsystem li.pluto span {
  background: #7c6a5c;
  top: 69px;
  left: 79px;
}

/* CSS3 Animations */
ul.solarsystem li {
  animation-iteration-count: infinite;
  animation-timing-function: linear;
  animation-name: orbit;
}
ul.solarsystem li.earth span {
  animation-iteration-count: infinite;
  animation-timing-function: linear;
  animation-name: moon;
}
ul.solarsystem li.mercury {
  animation-duration: 5s;
}
ul.solarsystem li.venus {
  animation-duration: 8s;
}
ul.solarsystem li.earth {
  animation-duration: 12s;
}
ul.solarsystem li.earth span {
  animation-duration: 2s;
}
ul.solarsystem li.mars {
  animation-duration: 20s;
}
ul.solarsystem li.asteroids_meteorids {
  animation-duration: 50s;
}
ul.solarsystem li.jupiter {
  animation-duration: 30s;
}
ul.solarsystem li.saturn {
  animation-duration: 60s;
}
ul.solarsystem li.uranus {
  animation-duration: 70s;
}
ul.solarsystem li.neptune {
  animation-duration: 100s;
}
ul.solarsystem li.pluto {
  animation-duration: 120s;
}

@keyframes orbit {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}
@keyframes moon {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}

/* ul.solarsystem:hover  */
li:hover {
  animation-play-state: paused;
}

.slide-fade-enter-active {
  transition: all 0.3s ease;
}
.slide-fade-leave-active {
  transition: all 0.3s ease;
}
.slide-fade-enter, .slide-fade-leave-to
/* .slide-fade-leave-active below version 2.1.8 */ {
  transform: translateX(10px);
  opacity: 0;
}

.slide-fade-leave-to {
  transform: translateX(-10px);
  opacity: 0;
}
</style>
