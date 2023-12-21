<template>
    <div class="col-md-8" v-if="showColorPickerComponent">
        <div class="text-center mb-5">
            <h3>Color Picker Tool</h3>
        </div>
        <div class="form-group">
            <label>Child Count:</label>
            <input type="color" v-model="selectedColor" @input="updateColor" class="form-control" style="height: 200px;" title="Click to select color">
        </div>
        <div class="form-group mt-3">
            <label>Color Format:</label>
            <select class="form-select" v-model="colorFormat">
                <option value="">-- Please select --</option>
                <option value="hex">Hex Code</option>
                <option value="rgba">RGBA</option>
            </select>
        </div>
        
        <div v-if="selectedColor" class="mt-3">
            <h5>Selected Color Code:</h5>
            <div v-if="colorFormat === 'hex'">
                <textarea style="font-weight: bold; font-size: 30px" class="form-control text-center p-5" rows="1" readonly>{{ selectedColor }}</textarea>
            </div>
            <div v-if="colorFormat === 'rgba'">
                <textarea style="font-weight: bold; font-size: 30px" class="form-control text-center p-5" rows="1" readonly>{{ convertToRGBA(selectedColor) }}</textarea>
            </div>
            <div class="d-flex justify-content-center mt-2">
                <button @click="copyColorCode" class="btn btn-warning">Copy Color Code</button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: ['showColorPickerComponent'],
  data() {
    return {
      selectedColor: '#000000',
      colorFormat: 'hex',
    };
  },
  methods: {
    updateColor(event) {
      this.selectedColor = event.target.value;
    },
    convertToRGBA(hex) {
      // Convert hex to RGBA
      const bigint = parseInt(hex.substring(1), 16);
      const r = (bigint >> 16) & 255;
      const g = (bigint >> 8) & 255;
      const b = bigint & 255;
      return `rgba(${r}, ${g}, ${b}, 1)`;
    },
    copyColorCode() {
      const colorCode = this.colorFormat === 'hex' ? this.selectedColor : this.convertToRGBA(this.selectedColor);
      const textarea = document.createElement('textarea');
      textarea.value = colorCode;
      document.body.appendChild(textarea);
      textarea.select();
      document.execCommand('copy');
      document.body.removeChild(textarea);
    },
  },
};
</script>