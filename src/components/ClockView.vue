<template>
      <canvas ref="canvasRef" class="canvas" height="500" width="500"></canvas>
</template>

<script setup>
     import {ref,onMounted} from 'vue'
     const canvasRef = ref(null)
     onMounted(()=>{
         setInterval(()=>{
             clockMethod();
         },1000)

     })

     let clockMethod =()=>{
         if(canvasRef.value){
             const ctx = canvasRef.value.getContext("2d");
             ctx.clearRect(0,0,canvasRef.value.width,canvasRef.value.height);
             ctx.beginPath();
             ctx.arc(250,250,200,0,Math.PI*2);
             ctx.clip();
               //设置背景图片
               let imag = new Image();
               imag.src = "http://gips3.baidu.com/it/u=3886271102,3123389489&fm=3028&app=3028&f=JPEG&fmt=auto?w=1280&h=960";
               imag.onload = function () {
                     ctx.drawImage(imag,0,0,500,500);
                     ctx.strokeStyle="#03E3F6";
                     ctx.lineWidth="10";
                     ctx.stroke();
                     ctx.closePath();
                     ctx.save();
                     //设置圆心点为0,0
                     ctx.translate(250,250);
                     //画小时刻度,12个小时，使用for循环
                     for(let i=0;i<12;i++){
                           ctx.beginPath();
                           ctx.moveTo(0,-195);
                           ctx.lineTo(0,-175);
                           ctx.lineWidth="7";
                           ctx.strokeStyle="yellow";
                           ctx.stroke();
                           ctx.rotate(30*Math.PI/180);
                           ctx.closePath();
                     }
                     ctx.restore();

                     //画分钟刻度，一共60个，360/60=6度
                     ctx.save();
                     //设置圆心点为0,0
                     ctx.translate(250,250);
                     for(let i=0;i<60;i++){
                           ctx.beginPath();
                           ctx.moveTo(0,-195);
                           ctx.lineTo(0,-185);
                           ctx.lineWidth="4";
                           ctx.strokeStyle="yellow";
                           ctx.stroke();
                           ctx.rotate(6*Math.PI/180);
                           ctx.closePath();
                     }
                     ctx.restore();

                     let date = new Date();
                     let min = date.getMinutes();
                     let hou = date.getHours()>12?date.getHours()-12:date.getHours();
                     hou+= (min/60);
                     let sec = date.getSeconds();

                     //画小时线，起点是中心点
                     ctx.save();
                     //设置圆心点为0,0
                     ctx.translate(250,250);
                     ctx.beginPath();
                     ctx.rotate(hou*30*(Math.PI/180));
                     ctx.moveTo(0,0);
                     ctx.lineTo(0,-125);
                     ctx.lineWidth="6";
                     ctx.strokeStyle="#03E3F6";
                     ctx.stroke();
                     ctx.closePath();
                     ctx.restore();

                     //画分钟线，起点是中心点
                     ctx.save();
                     //设置圆心点为0,0
                     ctx.translate(250,250);
                     ctx.beginPath();
                     ctx.rotate(min*6*(Math.PI/180));
                     ctx.moveTo(0,0);
                     ctx.lineTo(0,-145);
                     ctx.lineWidth="4";
                     ctx.strokeStyle="yellow";
                     ctx.stroke();
                     ctx.closePath();
                     ctx.restore();

                     //画秒线，起点是中心点
                     ctx.save();
                     //设置圆心点为0,0
                     ctx.translate(250,250);
                     ctx.beginPath();
                     ctx.rotate(sec*6*(Math.PI/180));
                     ctx.moveTo(0,10);
                     ctx.lineTo(0,-165);
                     ctx.lineWidth="3";
                     ctx.strokeStyle="red";
                     ctx.stroke();
                     ctx.closePath();
                     //头部圆圈
                     ctx.beginPath();
                     ctx.arc(0,-145,5,0,Math.PI*2);
                     ctx.fillStyle="yellow";
                     ctx.fill();
                     ctx.strokeStyle="red";
                     ctx.stroke();
                     ctx.closePath();
                     //底部圆圈
                     ctx.beginPath();
                     ctx.arc(0,0,5,0,Math.PI*2);
                     ctx.fillStyle="yellow";
                     ctx.fill();
                     ctx.strokeStyle="red";
                     ctx.stroke();
                     ctx.closePath();
                     ctx.restore();
               }
         }
     }
</script>
<style>
    .canvas{
        border: 1px solid red;
        background-color: black;
    }
</style>