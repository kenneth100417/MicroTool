
<template>
    <div class="col-md-8" v-if="showQrCodeGeneratorComponent">
        <div class="text-center mb-5">
            <h3>QR Code Generator Tool</h3>
        </div>
        <div class="form-group">
            <label style="font-weight: bold;">QR Code Content:</label>
            <input type="text"  v-model="content" class="form-control mt-2">
            <div class="mt-3 d-flex justify-content-center">
                <button class="btn btn-primary" @click="generateQRCode">Generate QR Code</button>
            </div>
        </div>
        
        <div v-if="qrCode">
            <div class="mt-5 d-flex justify-content-center" >
                <div style="width: 400px; height: 400px;" class="bg-dark bg-opacity-10 d-flex justify-content-center border border-3 border-dark text-center">
                    <img :src="qrCode" alt="Generated QR Code"/>
                </div>
            </div>
            <div class="d-flex justify-content-center mt-2">
                <button @click="downloadQRCode" class="btn btn-warning">Download QR Code</button>
            </div>
        </div>


    </div>
</template>


<script>
import QRCode from 'qrcode';
 
  export default {
    props: ['showQrCodeGeneratorComponent'],
    components: {
    },
    data() {
    return {
      content: '',
      qrCode: null,
    };
  },
  methods: {
    generateQRCode() {
      if (this.content.trim() !== '') {
        // Generate QR code
        QRCode.toDataURL(this.content, (err, url) => {
          if (err) console.error(err);
          else this.qrCode = url;
        });
      }
    },
    downloadQRCode() {
      if (this.qrCode) {
        const downloadLink = document.createElement('a');
        downloadLink.href = this.qrCode;
        downloadLink.download = 'qrcode.png';
        document.body.appendChild(downloadLink);
        downloadLink.click();
        document.body.removeChild(downloadLink);
      }
    },
  },
  }



</script>