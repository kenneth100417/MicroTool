<template>
    <div class="col-md-8" v-if="showRandomNamePickerComponent">
        <div class="text-center mb-5">
            <h3>Countdown Timer</h3>
        </div>
        <div class="form-group" v-if="!isRunning">
            <label style="font-weight: bold;">Enter names:</label>
            <input type="text" id="inputNames" v-model="inputNames" min="1" :disabled="isRunning" class="form-control mt-2" placeholder="Input names separated by commas (',')">
        </div>
        <div class="d-flex justify-content-center p-3">
            <div >
                <button class="btn btn-primary m-1" @click="startPicker" :disabled="isRunning || !isValidInput">Pause</button>
                <button class="btn btn-danger m-1" @click="stopPicker" :disabled="!isRunning">Stop</button>
            </div>
        </div>

        <div v-if="isRunning" class="mt-3">
            <h5>Randomly Selected Name:</h5>
            <H1 style="font-weight: bold; font-size: 60px" class="form-control text-center p-5" rows="1" readonly>
            {{ selectedName }}</h1>
        </div>

        <audio ref="audioNotification" src="src\assets\notifications\end.wav"></audio>
             
    </div>
</template>

<script>
export default {
  props: ['showRandomNamePickerComponent'],
  data() {
    return {
      inputNames: '',
      isRunning: false,
      selectedName: '',
      intervalId: null,
    };
  },
  computed: {
    isValidInput() {
      // Check if inputNames contain at least one name
      return this.inputNames.trim().length > 0;
    },
    namesArray() {
      // Split inputNames into an array of names
      return this.inputNames.split(',').map(name => name.trim());
    },
  },
  methods: {
    startPicker() {
      if (this.isValidInput && !this.isRunning) {
        this.isRunning = true;

        this.intervalId = setInterval(() => {
          const randomIndex = Math.floor(Math.random() * this.namesArray.length);
          this.selectedName = this.namesArray[randomIndex];
        }, 5000);
      }
    },
    stopPicker() {
      clearInterval(this.intervalId);
      this.isRunning = false;
    },
  },
  beforeDestroy() {
    clearInterval(this.intervalId);
  },
};
</script>