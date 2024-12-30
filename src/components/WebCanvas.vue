<template>
    <canvas class="canvas" width="600px" height="600px" ref="canvasRef"></canvas>
</template>
<script setup>
    import { ref,onMounted } from "vue"
    const canvasRef = ref(null)
    onMounted(()=>{
        if(canvasRef.value){
            const ctx = canvasRef.value.getContext("2d")
            //直线，起始点，终点
           /* ctx.moveTo(100,0);
            ctx.lineTo(200,50);
            ctx.strokeStyle="red";
            ctx.lineWidth = "5";
            ctx.stroke();*/

            //三角形，起始点，下一个点，下一个点，回到起始点
         /*   ctx.moveTo(100,0);
            ctx.lineTo(200,50);
            ctx.lineTo(50,50);
            ctx.lineTo(100,0);
            ctx.strokeStyle="red";
            ctx.lineWidth = "5";
            ctx.fillStyle="blue";
            ctx.fill();
            ctx.stroke();*/

            //两个三角形
            /*ctx.beginPath();
            ctx.moveTo(100,0);
            ctx.lineTo(110,10);
            ctx.lineTo(90,10);
            ctx.lineTo(100,0);
            ctx.strokeStyle="red";
            ctx.fillStyle="blue";
            ctx.fill();
            ctx.stroke();
            ctx.closePath();
            ctx.beginPath();
            ctx.moveTo(100,20);
            ctx.lineTo(110,30);
            ctx.lineTo(90,30);
            ctx.lineTo(100,20);
            ctx.strokeStyle="pink";
            ctx.fillStyle="yellow";
            ctx.fill();
            ctx.stroke();
            ctx.closePath();*/

            //多边形
           /* ctx.beginPath();
            ctx.moveTo(100,40);
            ctx.lineTo(110,40);
            ctx.lineTo(120,45);
            ctx.lineTo(110,50);
            ctx.lineTo(100,50);
            ctx.lineTo(95,45);
            ctx.lineTo(100,40);
            ctx.strokeStyle="pink";
            ctx.fillStyle="yellow";
            ctx.fill();
            ctx.stroke();
            ctx.closePath();*/

           //矩形
            /*ctx.beginPath();
            ctx.rect(30,30,100,100);
            ctx.fillStyle="yellow";
            ctx.stroke();
            ctx.closePath();*/
            //带边框的矩形，便捷写法
            //ctx.strokeRect(30,30,100,100);
            //带填充色的矩形，便捷写法
          /*  ctx.fillStyle="red";
            ctx.fillRect(30,30,100,100);*/

          //清除矩形,clearRect
            /*ctx.fillStyle="red";
            ctx.fillRect(30,30,100,100);
            ctx.clearRect(32,32,10,10);*/

            //圆形
          /*  ctx.beginPath();
            ctx.arc(200,200,100,0,Math.PI*2,true);
            ctx.fillStyle="red";
            ctx.fill();
            ctx.stroke();
            ctx.closePath();*/
            //半圆
          /*  ctx.beginPath();
            ctx.arc(200,200,100,0,Math.PI,false);
            ctx.fillStyle="red";
            ctx.fill();
            ctx.stroke();
            ctx.closePath();*/

          //二次贝赛尔曲线
        /*    ctx.moveTo(0,200);
            ctx.quadraticCurveTo(100,30,200,200);
            ctx.stroke();*/

          //三次贝赛尔曲线
           /* ctx.moveTo(0,200);
            ctx.bezierCurveTo(50,20,150,300,200,200);
            ctx.stroke();*/

           //移动
            ctx.save();
            ctx.fillStyle="red";
            ctx.translate(100,300);
            ctx.scale(1,2);
            ctx.rotate(30);
            ctx.fillRect(30,30,100,100);
            ctx.restore();
            ctx.save();
            ctx.fillStyle="blue";
            ctx.translate(100,100);
            ctx.fillRect(30,30,100,100);
            ctx.restore();
        }
    })


</script>
<style>
    .canvas{
        border: 1px solid red;
    }
</style>