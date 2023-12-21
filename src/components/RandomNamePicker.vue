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
                <button class="btn btn-primary m-1" @click="startPicker" :hidden="isRunning || !isValidInput">Start Picking</button>
                <button class="btn btn-danger m-1" @click="stopPicker" :hidden="!isRunning">Pick Another</button>
            </div>
        </div>

        <div v-if="isRunning" class="mt-3">
            <h5>Randomly Selected Name:</h5>
            <H1 style="font-weight: bold; font-size: 60px" class="form-control text-center p-5" rows="1" readonly>
            {{ selectedName }}</h1>
        </div>
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
      remainingNames: [],
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
        this.remainingNames = [...this.namesArray];
          if (this.remainingNames.length > 0) {
            const randomIndex = Math.floor(Math.random() * this.remainingNames.length);
            this.selectedName = this.remainingNames.splice(randomIndex, 1)[0];
          } else {
            this.stopPicker();
          }
       
      }
    },
    stopPicker() {
      clearInterval(this.intervalId);
      this.isRunning = false;
      this.selectedName = '';
      this.remainingNames = [];
    },
  },
  beforeDestroy() {
    clearInterval(this.intervalId);
  },
};
</script>