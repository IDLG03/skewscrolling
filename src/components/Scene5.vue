<template>
    <div>
        <div class="homescreen-bg">
        </div>
        <div class="homescreen-body">
            <div class="homescreen-body-inner" id="scene5-inner">
                <h1 class="content">Lorem Ipsum</h1>
                <p class="content">Lorem ipsum dolor sit amet, <br>
                    consectetur adipiscing elit. Duis in posuere nibh, <br>
                    eget blandit nisl. Nulla fermentum sem nulla, <br>
                    aliquam bibendum nisl laoreet ut. Morbi mauris arcu, <br>
                    tristique ut dolor id, auctor hendrerit mi.</p>
            </div>            
        </div>        
    </div>
</template>

<script>
export default {
    name: 'Scene5',
    props: {
        
    },
    data() {
        return {   

        }
    },
}
</script>

<style scoped>

.homescene {
    width: 100%;
    height: 100%;  
    position: absolute;
    visibility: hidden;
    top: 0;
    left: 0;
    z-index: 1;
    opacity: 0;
    align-items: center;
    overflow: hidden;
}
.homescreen-bg {
    position: absolute;
    width: auto;
    height: auto;
    max-width: none;
    min-width: 100%;
    min-height: 100%;
}
.homescreen-body {
    display: flex;
    align-items: center;  
    position: absolute;
    width: 100%;
    height: 100%;
    left: 0;
    top: 0;
}
.homescreen-body-inner {
    width: 100%;
    margin-left: 50%;
    margin-right: 15%;
    text-align: left;
    color: whitesmoke;
    font-family:serif;
    line-height: 2;
    letter-spacing: 0.5px;
}
#scene5 {
  z-index: 0;
}
#scene5-inner {
  text-align: center;
  margin-left: 10%;
  margin-right: 10%;
  color: black;
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
img {
    position: absolute;
    left: 0;
    width: auto;
    height: auto;
    max-width: 100%;  
    min-height: 100%;
    object-fit: fill;
    display: inline-block;
}
h1 {
    font-size: 36px;
    position: relative;  
    overflow: hidden;
    margin: 0;
    color: #dc0032;
}
p {
    overflow: hidden;
    font-size: 15px;
    margin-top: 0;
}
div {
    display: block;
}
@media screen and (max-width: 700px) {
    .homescreen-body-inner{
        margin-left: 10%;
        margin-right: 10%;
        width: 100%;
    }    
    img {
        position: absolute;    
        height: auto;
        width: auto;
        left: -50%;    
        max-width: none;
        max-height: 100%;
        min-width: 100%;
        min-height: 100%;
        vertical-align: middle;
    }
}
</style>
