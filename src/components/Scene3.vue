<template>
    <div>
        <div class="homescreen-bg">
            <img src="../assets/3.jpg" alt="">            
        </div>
            <div class="homescreen-body">
                <div class="homescreen-body-inner">
                    <h1 class="content">Lorem ipsum</h1>
                    <p class="content">Lorem ipsum dolor sit amet, <br>
                        consectetur adipiscing elit. Duis in posuere nibh, <br>
                        eget blandit nisl. Nulla fermentum sem nulla, <br>
                        aliquam bibendum nisl laoreet ut. Morbi mauris arcu, <br>
                        tristique ut dolor id, auctor hendrerit mi.</p>
                    <div class="content">
                        <a href="">READ MORE >>></a>
                    </div>
                </div>                
            </div>
    </div>
</template>

<script>
export default {
    name: 'Scene3',
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
a {
    display: inline-block;
    position: relative;
    padding: 10px 15px 10px 15px;
    background: #dc0032;
    background: linear-gradient(135deg,white 50%,#dc0032 50%);
    background-size: 100% 500%;
    background-position: bottom ;
    text-decoration: none;
    color: white;
    transition: all .5s ease;    
}
a:hover {
    color: #dc0032;
    background-position: top;    
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
