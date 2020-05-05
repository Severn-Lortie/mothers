<template>
<div>
    <div class="camera-button">
        <camera-button @clicked="clicked" />
    </div>
    <div class="container-center">
        <img :src="cameraSvg" class="svg-size">
        <div class="camera-message">
            <!-- The camera message component will display in here -->
            <slot name="message"></slot>
        </div>
    </div>
</div>
</template>

<script>
import cameraSvgUnpressed from '../assets/camera-back.svg';
import cameraSvgLoading from '../assets/camera-back-loading.svg';

// shutter sound effect
import shutterSound from '../assets/shutter.mp3';

export default {
    totalMessages: 30,
    cameraSvgMessages: {},
    audio: new Audio(shutterSound),

    data() {
        return {
            cameraSvg: cameraSvgUnpressed,
            counter: 0,
            canClick: true
        }
    },
    components: {
        cameraButton: () => import('./CameraButton')
    },
    methods: {
        clicked() {
            // this sets the display to loading when the button is pressed
            this.cameraSvg = cameraSvgLoading;

            // play the shutter sound
            this.$options.audio.play();

            if (this.counter < this.$options.totalMessages && this.canClick) {
                this.canClick = false;
                setTimeout(async () => {
                    let message = await this.$options.cameraSvgMessages[`svg-${this.counter}`];
                    this.cameraSvg = message.default;
                    this.counter++;
                    this.canClick = true;
                }, 1000);
            }
        }
    },
    created() {
        // load in the messages
        for (let i = 0; i < this.$options.totalMessages; i++) {
            this.$options.cameraSvgMessages[`svg-${i}`] = import(`../assets/camera-back-message-${i + 1}.svg`);
        }
    }
}
</script>

<style scoped>
.svg-size {
    position: relative;
    width: auto;
    height: 80vh;
    bottom: 5vh;
}

.container-center {
    text-align: center;
}

.camera-button {
    text-align: center;
    margin-top: 10vh;
    z-index: 999;
    position: relative;
}
</style>
