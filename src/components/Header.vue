<template>
    <div class="header">        
        <div class="header-content">
            <h1>TEST SITE</h1>
        <img src="../assets/elements.png" alt="">
        </div>
        
    </div>
</template>

<script>
export default{
    name: 'Header',
    data() {
        return {

        }
    },
}
</script>

<style scoped>
.header {
    position: absolute;
    display: flex;
    align-items: center;
    top: 0;
    left: 0;
    z-index: 4;
    height: 100px;    
    padding-left: 5%;
}
h1 {
    font-family: serif;
    color: lightblue;
    margin: 0;
}
img {    
    height: 20px;
    right: calc(10% + 250px);
}
.header-content :hover {
    
    filter: brightness(150%);
}
</style>