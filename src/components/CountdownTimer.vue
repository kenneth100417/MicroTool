<template>
    <div class="col-md-8" v-if="showCountdownTimerComponent">
        <div class="text-center mb-5">
            <h3>Countdown Timer</h3>
        </div>
        <div class="form-group" v-if="!isRunning">
            <label style="font-weight: bold;">Duration (seconds):</label>
            <input type="number" id="duration" v-model="duration" min="1" :disabled="isRunning" class="form-control mt-2" placeholder="Input timer duration">
        </div>
        <div class="d-flex justify-content-center p-3">
            <div v-if="!isRunning">
                <button class="btn btn-success m-1" @click="startTimer" :disabled="duration <= 0">Start</button>
            </div>
            <div v-else>
                <button class="btn btn-primary m-1" @click="pauseTimer">Pause</button>
                <button class="btn btn-danger m-1" @click="stopTimer">Stop</button>
            </div>
            <button class="btn btn-warning m-1" @click="resetTimer" :disabled="!isRunning">Reset</button>
        </div>

        <div v-if="isRunning" class="mt-3">
            <h5>Time Remaining:</h5>
            <H1 style="font-weight: bold; font-size: 60px" class="form-control text-center p-5" rows="1" readonly>
            {{ formatTime(remainingTime) }}</h1>
        </div>

        <audio ref="audioNotification" src="src\assets\notifications\end.wav"></audio>
             
    </div>
</template>


<script>
export default {
    props: ['showCountdownTimerComponent'],
  data() {
    return {
      duration: 60, // Initial duration in seconds
      isRunning: false,
      remainingTime: 0,
      intervalId: null,
    };
  },
  methods: {
    startTimer() {
      if (this.duration > 0 && !this.isRunning) {
        this.isRunning = true;
        this.remainingTime = this.duration;

        this.intervalId = setInterval(() => {
          if (this.remainingTime > 0) {
            this.remainingTime--;
          } else {
            this.playNotificationSound();
            this.stopTimer();
          }
        }, 1000);
      }
    },
    pauseTimer() {
      clearInterval(this.intervalId);
      this.isRunning = false;
    },
    stopTimer() {
      clearInterval(this.intervalId);
      this.isRunning = false;
      this.remainingTime = 0;
    },
    resetTimer() {
      this.stopTimer();
      this.remainingTime = this.duration;
    },
    formatTime(seconds) {
      const minutes = Math.floor(seconds / 60);
      const remainingSeconds = seconds % 60;
      return `${minutes}:${remainingSeconds < 10 ? '0' : ''}${remainingSeconds}`;
    },
    playNotificationSound() {
      const audioElement = this.$refs.audioNotification;
      audioElement.play();
    },
  },
  beforeDestroy() {
    clearInterval(this.intervalId);
  },
};
</script>