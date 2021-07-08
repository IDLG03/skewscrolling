<template>
    <section>
        <div class="homescreen-bg">
            <img src="../assets/1.png" alt="" class="bg">
        </div>
        <div class="homescreen-body">
            <div class="homescreen-body-inner">
                
                <div class="content">
                    <img src="../assets/genshinlogo.png" alt="" id="title">
                </div>
                
            
            
            </div>
        </div>          
    </section>
</template>

<script>
export default {
    name: 'Scene1',
    props: {
        
    },
    data() {
        return {   

        }
    },
}
</script>

<style scoped>

#title {
    position: absolute;    
    left: calc(50% - 25%);
    width: 50%;
    height: auto;
    object-fit: contain;
}
.content {
    height: 300px;
    
}
.homescene {
    width: 100%;
    height: 100%;  
    position: absolute;
    visibility: visible;
    top: 0;
    left: 0;
    z-index: 1;
    opacity: 1;
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
    margin-left: 15%;
    margin-right: 15%;
    text-align: center;
    color: whitesmoke;
    font-family:serif;
    
    letter-spacing: 0.5px;
}
img {
    position: absolute;
    left: 0;
    width: 100%;
    height: auto;
    max-width: 100%;  
    min-height: 100%;
    object-fit: fill;
    display: inline-block;
}
h1 {
    font-size: 50px;
    position: relative;  
    overflow: hidden;
    margin: 0;
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
    .homescreen-bg {
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
    .bg {
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
    #title {
    position: absolute;    
    left: 0%;
    width: 50%;
    height: auto;
    object-fit: contain;
}
}
</style>
