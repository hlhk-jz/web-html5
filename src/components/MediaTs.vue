<template>
    <div class="video-player">
        <video class="v1" ref="videoRef" @timeupdate="updateProgress" @ended="onVideoEnded">
           <source class="v2" src="@/assets/file/m1.mp4"/>
        </video>
        <div class="controls">
            <!-- 播放/暂停按钮 -->
            <button @click="togglePlayPause">{{ isPlaying ? '暂停' : '播放' }}</button>
            <!-- 进度条 -->
            <input type="range" v-model="currentTime" @input="seek" min="0" :max="duration">
            <!-- 音量控制 -->
            <input type="range" v-model="volume" @input="setVolume" min="0" max="1" step="0.1">
            <!-- 全屏按钮 -->
            <button @click="toggleFullscreen">全屏</button>
        </div>
    </div>
</template>

<script setup>
    import { ref, onMounted } from 'vue';

    // 视频源
    //const videoSrc = ref('https://commondatastorage.googleapis.com/gtv-videos-bucket/sample/BigBuckBunny.mp4');
    // 视频元素引用
    const videoRef = ref(null);
    // 是否正在播放
    const isPlaying = ref(false);
    // 当前播放时间
    const currentTime = ref(0);
    // 视频总时长
    const duration = ref(0);
    // 音量
    const volume = ref(1);

    // 挂载完成后初始化视频
    onMounted(() => {
        const video = videoRef.value;
        video.addEventListener('loadedmetadata', () => {
            duration.value = video.duration;
        });
    });

    // 切换播放/暂停状态
    const togglePlayPause = () => {
        const video = videoRef.value;
        if (isPlaying.value) {
            video.pause();
        } else {
            video.play();
        }
        isPlaying.value = !isPlaying.value;
    };

    // 更新进度条
    const updateProgress = () => {
        const video = videoRef.value;
        console.log("进度条：",video.currentTime)
        currentTime.value = video.currentTime;
    };

    // 拖动进度条跳转
    const seek = () => {
        const video = videoRef.value;
        video.currentTime = currentTime.value;
    };

    // 设置音量
    const setVolume = () => {
        const video = videoRef.value;
        video.volume = volume.value;
    };

    // 切换全屏
    const toggleFullscreen = () => {
        const video = videoRef.value;
        if (video.requestFullscreen) {
            video.requestFullscreen();
        } else if (video.webkitRequestFullscreen) { /* Safari */
            video.webkitRequestFullscreen();
        } else if (video.msRequestFullscreen) { /* IE11 */
            video.msRequestFullscreen();
        }
    };

    // 视频播放结束处理
    const onVideoEnded = () => {
        isPlaying.value = false;
        currentTime.value = 0;
    };
</script>

<style scoped>
    .video-player {
        position: relative;
        width: 500px;
        height: 360px;
    }
    .v1{
        width: 100%;
        height: 200px;
    }
    .v2{
        width: 100%;
        height: 100%;
    }

    .controls {
        position: absolute;
        bottom: 0;
        left: 0;
        right: 0;
        background-color: rgba(0, 0, 0, 0.7);
        color: white;
        display: flex;
        align-items: center;
        padding: 5px;
    }

    .controls button {
        background: none;
        border: none;
        color: white;
        cursor: pointer;
        margin: 0 5px;
    }

    .controls input[type="range"] {
        flex: 1;
        margin: 0 5px;
    }
</style>