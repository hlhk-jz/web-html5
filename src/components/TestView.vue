<template>
    <div class="layout">
        <!--<div class="tr1">
            <div>
                <img src="../assets/logo.png" class="img"/>
            </div>
        </div>

        <div class="tr2">
            <div class="tr3">
                <img src="../assets/logo.png"  class="img img3d"/>
            </div>
        </div>-->

       <!-- <div class="div1">

        </div>-->
       <!-- <div class="div2">

        </div>-->
        <div class="div8">
            <div class="div81"></div>
            <!--<div class="div81"></div>
            <div class="div81"></div>-->
        </div>
    </div>
</template>

<style>
    .div8{
        /*display: flex;*/
        width: 300px;
        height: 300px;
        border: 1px solid blue;

        /*justify-content: center;
        align-items: center;*/
     /*   position: relative;*/
    }
    .div81{
        width: 40px;
        height: 40px;
        border: 1px solid black;
        margin: auto;
       /* position: absolute;
        left: 50%; top: 50%; transform: translate(-50%, -50%);*/

    }
  .layout{
      width: 600px;
      height: 500px;
      border: 1px solid red;
      position: relative;
      perspective: 500px;
  }
  .div2{
      width: 50px;
      height: 50px;
      background-color: red;
      animation: name1 10s infinite;
  }
  @keyframes name1 {
      0%{
          width: 100px;
          height: 100px;
          background-color: black;
      }
      20%{
          width: 50px;
          height: 100px;
          background-color: red;
      }
      60%{
          width: 200px;
          height: 200px;
          background-color: yellow;
      }
      100%{
          width: 100px;
          height: 100px;
          background-color: black;
      }
  }

  .div1{
      height: 50px;
      width: 50px;
      background-color: blue;
      transition: width 3s 1s ease;
  }
  .div1:hover{
      width: 200px;
  }

  /*3D效果*/
  .tr1{
      width: 100px;
      height: 100px;
      border: 1px solid blue;
      background-color: blue;
      position: absolute;
      top: 100px;
      left: 100px;
      transform-style: preserve-3d;
 }
  .tr3{
      transform-style: preserve-3d;
  }
  .tr2{
      width: 100px;
      height: 100px;
      border: 1px solid blue;
      background-color: blue;
      position: absolute;
      top: 100px;
      left: 300px;
  }
  .img{
      width: 100%;
      height:100%;

  }
  .img3d{
     /* transform: translate3d(50px,50px,50px);*/
      transform: rotate3d(1,1,1,60deg);

  }

    /*.tr1{
        width: 100px;
        height: 100px;
        border: 1px solid blue;
        background-color: blue;
        position: absolute;
        top: 100px;
        left: 100px;
        transform: rotate(60deg);
        transform-origin: bottom;
    }
    .tr2{
        width: 100px;
        height: 100px;
        border: 1px solid blue;
        background-color: blue;
        position: absolute;
        top: 100px;
        left: 300px;
        transform: rotate(60deg);
    }*/
</style>