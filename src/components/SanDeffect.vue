<template>
    <div class="layout">
        <div class="text"><h1>3D效果</h1></div>
        <div class="imgDiv">
            <img class="img hov"  src="../assets/sy1.jpeg"/>
        </div>
    </div>
</template>

<style>
    .layout{
        width: 600px;
        height: 600px;
        border: 1px solid red;
        box-sizing: border-box;
    }
    .text{
        text-align: center;
      }
    .imgDiv{
        width: 100%;
        height: 500px;
        transform-style: preserve-3d;
        perspective: 1500px;
    }
    .img{
        width: 60%;
        height: 60%;
        margin: 50px auto 0;
        display: block;
        box-shadow: -6px 5px 7px ;
        transform: rotateX(40deg) rotateZ(30deg);
        transition: all 3s ease;
    }
    .hov:hover{
        box-shadow: -60px 50px 70px white;
        transform: rotate3d(0,0,0,0deg);
    }
</style>