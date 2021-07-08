<template>
  <div class="content-container"  >
    
    <div class="homescreen" v-on:wheel.once.self="handleWheel" >
      <transition-group                
				v-on:enter="enter"				
				v-on:leave="leave"
				mode="out-in"
      >
        <section class="homescene" id="scene1" v-if="scene === 1" :key="scene" >
          <Scene1 />          
        </section>

        <section class="homescene" id="scene2" v-else-if="scene === 2" :key="scene" >
          <Scene2 />
        </section>

        <section class="homescene" id="scene3" v-else-if="scene === 3" :key="scene" >
          <Scene3 />
        </section>

        <section class="homescene" id="scene4" v-else-if="scene === 4" :key="scene" >
          <Scene4 />
        </section>

        <section class="homescene" id="scene5" v-else-if="scene === 5" :key="scene" >
          <Scene5 />
          <div class="content" id="top-page" @click="topPage()">
            <div class="arrow">
              ^
            </div>
            <div class="text">
              PAGE TOP
            </div>                
          </div>  
        </section>

      </transition-group>
      <div class="line">
        <transition name="line-ani">
        <div class="line2" v-if="scene !==5"></div>
        </transition>
      </div>
      
    </div>

    <div class="navigation">
      <nav class="navi">
        <ul>
          <li v-bind:class= "{'highlight': scene1}" @click="scene = 1; currentscene()"><img src="../assets/pyro.png" alt="" class="icon"></li>
          <li v-bind:class= "{'highlight': scene2}" @click="scene = 2; currentscene()"><img src="../assets/hydro.png" alt="" class="icon"></li>
          <li v-bind:class= "{'highlight': scene3}" @click="scene = 3; currentscene()"><img src="../assets/anemo.png" alt="" class="icon"></li>
          <li v-bind:class= "{'highlight': scene4}" @click="scene = 4; currentscene()"><img src="../assets/electro.png" alt="" class="icon"></li>
          <li v-bind:class= "{'highlight': scene5}" @click="scene = 5; currentscene()"><img src="../assets/cryo.png" alt="" class="icon"></li>
        </ul>
      </nav>
    </div>
    <div class="content" id="scroll" @click="nextPage" v-if="scene === 1">
      SCROLL
      <div class="scroll-container">
      <div class="scroll-line">
        <div class="scroll-line2"></div>
      </div>        
      </div>
    </div>
    <div class="next" @click="nextPage" v-if="scene !== 5">
      V
    </div>

  </div>
</template>

<script>
import gsap from "gsap";
import debounce from 'lodash/debounce';
import Scene1 from '../components/Scene1.vue';
import Scene2 from '../components/Scene2.vue';
import Scene3 from '../components/Scene3.vue';
import Scene4 from '../components/Scene4.vue';
import Scene5 from '../components/Scene5.vue';
export default {
  name: 'HomePage',
  components: {
    Scene1,
    Scene2,
    Scene3,
    Scene4,
    Scene5,
  },
  props: {    
  },
  data() {
      return{
        isActive: true,
        activescene: null,
        scene1: null,
        scene2: null,
        scene3: null,
        scene4: null,
        scene5: null,                
        selected: null,
        changeSelected: null,
        scene: null,
        prevscene: 0,                      
      };      
      
  },  
  beforeDestroyed () {
    window.removeEventListener('wheel', this.handleDebouncedScroll);        
  },
  created() {
    this.handleDebouncedScroll = debounce(this.handleWheel, 500, {'leading':true, 'trailing': false} );  
    window.addEventListener('wheel', this.handleDebouncedScroll);
  },
  mounted() {    
    this.scene = 1;
    this.currentscene();
    console.log(this.scene);
    console.log("mount");
  },
  
  methods: {    
    currentscene() {
      this.scene1 = false;
      this.scene2 = false;
      this.scene3 = false;
      this.scene4 = false;
      this.scene5 = false;
      switch(this.scene) {
        case 1:
          this.scene1 = true;
          break;
        case 2:
          this.scene2 = true;
          break;
        case 3:
          this.scene3 = true;
          break;
        case 4:
          this.scene4 = true;
          break;
        case 5:
          this.scene5 = true;
          break;
      }
      
      return [
        this.scene1,
        this.scene2,
        this.scene3,
        this.scene4,
        this.scene5]
      
    },
    handleWheel(event) {      
        if (event.deltaY < 0) {
          this.scene = this.scene - 1;
          if(this.scene <= 1){
            this.scene = 1;
          }
          console.log("scrolling up")
        } 
        else if (event.deltaY > 0) {
          this.scene = this.scene + 1;
          if(this.scene >= 5){
            this.scene = 5;
          }
          console.log("scrolling down")
        }
        this.currentscene();
      console.log(event.deltaY);
    },        

    nextPage() {
      this.scene = this.scene + 1;
      if(this.scene >= 5){
        this.scene = 5;
      }
      this.currentscene();
      console.log("next page");
    },
    topPage(){      
      this.scene = 1;
      this.currentscene();
      console.log("top page");
    },    
    
		enter(el, done) {			
      //Scroll down enter animation
      if (this.scene > this.prevscene) {        
        gsap.fromTo(el, {     
        opacity: 1,
				y: '100%',
        x: '-15%',        
        },
        {
        delay: 1,
				opacity: 1,        
				y: 0,
        x: 0,
				duration: 1,				
        });
        //Background zoom in animation
        gsap.fromTo(el, {
          scale: 0.80,
        },
        {
        delay: 1.6,
        scale: 1,
        transformOrigin: '50% 50%',     
        onComplete: done,
      })
        //Text enter animation
        gsap.fromTo(".content", {
          scaleY: 0,
          opacity: 0,
        },
        {
          scaleY: 1,
          opacity: 1,
          transformOrigin: "50% bottom",
          delay: 2,
        })
      }
      //Scroll up enter animation
      else if (this.scene < this.prevscene){
        gsap.fromTo(el, {        
        opacity: 1,
				y: '-100%',
        x: '15%',        
        },
        {
        delay: 1,
				opacity: 1,        
				y: 0,
        x: 0,
				duration: 1,				
        });
        //Background zoom in animation
        gsap.fromTo(el, {
          scale: 0.80,
        },
        {
        delay: 1.6,
        scale: 1,
        transformOrigin: '50% 50%',        
        onComplete: done,
        })
        //Text enter animation
        gsap.fromTo(".content", {
          scaleY: 0,
          opacity: 0,
        },
        {
          scaleY: 1,
          opacity: 1,
          transformOrigin: "50% top",
          delay: 2,
        })
      }
      
			console.log("enter");
      console.log(this.scene);
      this.prevscene = this.scene;
		},		
		leave(el, done) {
      //Background zoom out animation
      gsap.fromTo(el,{
        scale: 1,
      },
      {
        scale: 0.8,
        transformOrigin: '50% 50%',
        delay: 0.7, 
      })
      //Scroll down leave animation
      if (this.scene > this.prevscene) {    
        gsap.fromTo(".content", {
          scaleY: 1,
          opacity: 1,
        },
        {
          scaleY: 0,
          opacity: 0,
          transformOrigin: "50% bottom",
          
        })
        gsap.to(el, {				
        opacity: 1,
        delay: 0.9,
				y: '-100%',
        x: '15%',
				duration: 1,
				onComplete: done,
        });
      }
      //Scroll up leave animation
      else if (this.scene < this.prevscene){
        gsap.fromTo(".content", {
          scaleY: 1,
          opacity: 1,
        },
        {
          scaleY: 0,
          opacity: 0,
          transformOrigin: "50% top",
          
        })
        gsap.to(el, {
				opacity: 1,
        delay: 0.9,
				y: '100%',
        x: '-15%',
				duration: 1,
				onComplete: done,
        });
      }      
			console.log("leave");
		},

    
  },
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.line {
  position: absolute;
  top: -25%;
  left: 50%;
  width: 2px;
  height: 50%;
  background: #dc0032;
  transform: rotate(15deg);
  transform-origin: center bottom;
}
.line2 {
  position: absolute;
  top: 0;
  
  width: 2px;
  height: 400%;
  background: #dc0032;
  transform-origin: center bottom;
}

.line-ani-enter {
  height: 100%;
}
.line-ani-enter-to {
  height: 400%;
}
.line-ani-enter-active {
  transition: all 1s ease 1s;
}
.line-ani-leave-from {
  height: 400%;
}
.line-ani-leave-to {
  height: 100%;
}
.line-ani-leave-active {
  transition: all 1s ease 1s;
}

.content-container {
  width: 100%;
  height: 100%;
  background: whitesmoke;
  position: absolute;
  top: 0;
  left: 0;
  overflow: hidden;
    
}

.homescreen {  
  z-index: 0;
  visibility: visible;
  opacity: 1;
}

.homescene {
  width: 100%;
  height: 100%;  
  position: absolute;
  top: 0;
  left: 0;
  z-index: 1;
  opacity: 1;
  align-items: center;
  overflow: hidden;
  
}

.navigation {
  z-index: 3;
  width: 50px;
  margin-right: 2.5%;
  position: absolute;
  top: calc(50% - 112.5px);
  right: 0;
  
}

.next {  
  z-index: 3;
  width: 45px;
  height: 45px;
  position: absolute;
  box-sizing: border-box;  
  bottom: 3%;
  right: 3%;
  border-radius: 50%;
  border: solid;
  border-color: whitesmoke;
  font-size: 40px;
  text-align: center;
  color: whitesmoke;
  opacity: 0.5;
}

.next:hover {
  opacity: 1;
}
#scroll {
  z-index: 3;
  width: 80px;
  height: 100px;
  position: absolute;
  left: calc(50% - 40px);
  bottom: -45px;
  color: gray;
  opacity: 0.5;
}
#scroll:hover {
  color: whitesmoke;
  
}
.scroll-line {
  position: absolute;
  left: calc(50% - .5px);
  width: 1px;
  height: 45px;
  background: whitesmoke;
}


#top-page {
  width: 90px;
  height: 40px;
  position: absolute;
  left: calc(50% - 45px);
  bottom: 5%;
  color: black;
}
#top-page:hover {  
  color: gray;
  
}
.arrow {
  position: absolute;
  width: 90px;
  height: 50px;
  font-size: 30px;
  z-index: 2;
}
.arrow:hover{
  top:-10px;
}
.text {
  position: absolute;
  top:25px;
  width: 90px;
  height: 25px;
}

div {
  display: block;
}
ul {
  list-style-type: none;
  padding: 0;  
}
li {
  display: inline-block;
  margin: 5px 10px;
  text-align: center;
  width: 25px;
  height: 25px;
  border-radius: 100%;
  border-style: solid;
  border-color: white;
  border-width: 1px;
  background: black;
  filter: brightness(50%);
}
li:hover {  
  filter: brightness(150%);
}
.highlight {  
  filter: brightness(150%);
}
.btn {
  background: gray;
}
.icon {
  width: 25px;
  height: 25px;
  filter: brightness(inherit);
}


a {
  color: #0d2018;
}
@media screen and (max-width: 700px) {  
  .navigation{
    visibility: hidden;
  }  
}
</style>
