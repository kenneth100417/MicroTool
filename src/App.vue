
<template>
  <header>
      <div class="d-flex justify-content-between align-items-center bg-dark text-white">
        <div class="p-4">
          <h4>K&K MicroTools</h4>
        </div>
        <div class="p-4" style="cursor: pointer;">
          <h4 @click="showAbout">About</h4>
        </div>
      </div>
  </header>
  <div class="container py-5" style="height: 100vh;">
    <div class="row">
      <div class="col-md-4">
          <div>
            <h4>MicroTools</h4>
          </div>
          <div class="card mt-3" style="width: 18rem;" :class="flexBox">
              <a @click="showFlexbox" class="text-decoration-none" >
                <div class="card-body">
                  <h5 class="card-title">Flexbox</h5>
                  <p class="card-text">A CSS layout module.</p>
                </div>
              </a>
          </div>
          <div class="card mt-3" style="width: 18rem;" :class="qrGen">
              <a @click="showQrGenerator" class="text-decoration-none" >
                <div class="card-body">
                  <h5 class="card-title">QR Code Generator</h5>
                  <p class="card-text">A tool to generate qr codes.</p>
                </div>
              </a>
          </div>
          <div @click="showPasswordGenerator" class="card mt-3" style="width: 18rem;" :class="passGen">
              <a href="javascript: void(0)" class="text-decoration-none">
                <div class="card-body">
                  <h5 class="card-title">Password Generator</h5>
                  <p class="card-text">A tool for generating random password.</p>
                </div>
              </a>
          </div>
          <div @click="showColorPicker" class="card mt-3" style="width: 18rem;" :class="colPicker">
              <a href="javascript: void(0)" class="text-decoration-none">
                <div class="card-body">
                  <h5 class="card-title">Color Picker</h5>
                  <p class="card-text">A tool for easy color picking.</p>
                </div>
              </a>
          </div>
          <div @click="showCountdownTimer" class="card mt-3" style="width: 18rem;" :class="countTimer">
              <a href="javascript: void(0)" class="text-decoration-none">
                <div class="card-body">
                  <h5 class="card-title">Countdown Timer</h5>
                  <p class="card-text">A countdown timer toool.</p>
                </div>
              </a>
          </div>
          <div @click="showRandomNamePicker" class="card mt-3" style="width: 18rem;" :class="namePicker">
              <a href="javascript: void(0)" class="text-decoration-none">
                <div class="card-body">
                  <h5 class="card-title">Random Name Picker</h5>
                  <p class="card-text">A countdown timer toool.</p>
                </div>
              </a>
          </div>
          <div class="my-3 mt-5">
            <h4>Mini Games</h4>
          </div>
          <div @click="showNinjaReactionTimer" class="card mt-3" style="width: 18rem;" :class="ninjaGame">
              <a href="javascript: void(0)" class="text-decoration-none">
                <div class="card-body">
                  <h5 class="card-title">Ninja Reacton Game</h5>
                  <p class="card-text">A game to test your reflexes.</p>
                </div>
              </a>
          </div>
      </div>
      <Flexbox :showFlexboxComponent="showFlexboxComponent"/>
      <QrCodeGenerator :showQrCodeGeneratorComponent = "showQrCodeGeneratorComponent"/>
      <PasswordGenerator :showPasswordGeneratorComponent="showPasswordGeneratorComponent"/> 
      <ColorPicker :showColorPickerComponent="showColorPickerComponent"/> 
      <NinjaReactionTimer :showNinjaReactionTimerComponent = "showNinjaReactionTimerComponent"/> 
      <CountdownTimer :showCountdownTimerComponent="showCountdownTimerComponent"/>
      <RandomNamePicker :showRandomNamePickerComponent="showRandomNamePickerComponent"/>
      <About :showAboutComponent = "showAboutComponent" />

    </div>
  </div>
</template>

<script>
  import Flexbox from './components/Flexbox.vue'
  import QrCodeGenerator from './components/QrCodeGenerator.vue'
  import PasswordGenerator from './components/PasswordGenerator.vue'
  import ColorPicker from './components/ColorPicker.vue'
  import NinjaReactionTimer from './components/NinjaReactionTimer.vue'
  import CountdownTimer from './components/CountdownTimer.vue'
  import RandomNamePicker from './components/RandomNamePicker.vue'
  import About from './components/About.vue'

  export default{
    components: {Flexbox, QrCodeGenerator, PasswordGenerator, ColorPicker, NinjaReactionTimer, CountdownTimer, RandomNamePicker, About},
    data(){
      return{
        showAboutComponent: false,
        showFlexboxComponent: true,
        showQrCodeGeneratorComponent: false,
        showPasswordGeneratorComponent: false,
        showColorPickerComponent: false,
        showNinjaReactionTimerComponent: false,
        showRandomNamePickerComponent: false,
        showCountdownTimerComponent: false,
        flexBox: 'active',
        qrGen: '',
        passGen: '',
        colPicker: '',
        countTimer: '',
        namePicker: '',
        ninjaGame: '',
      }
    },
    methods: {
      showAbout(){
        this.showAboutComponent = true
        this.showFlexboxComponent = false
        this.showQrCodeGeneratorComponent = false
        this.showPasswordGeneratorComponent = false
        this.showColorPickerComponent = false
        this.showNinjaReactionTimerComponent = false
        this.showCountdownTimerComponent = false
        this.showRandomNamePickerComponent = false
      },
      showFlexbox(){
        this.showAboutComponent = false
        this.showFlexboxComponent = true
        this.showPasswordGeneratorComponent = false
        this.showColorPickerComponent = false
        this.showQrCodeGeneratorComponent = false
        this.showNinjaReactionTimerComponent = false
        this.showCountdownTimerComponent = false
        this.showRandomNamePickerComponent = false
        this.flexBox = 'active'
        this.qrGen = ''
        this.passGen = ''
        this.colPicker = ''
        this.countTimer = ''
        this.namePicker = ''
        this.ninjaGame = ''

      },
      showQrGenerator(){
        this.showAboutComponent = false
        this.showFlexboxComponent = false
        this.showQrCodeGeneratorComponent = true
        this.showPasswordGeneratorComponent = false
        this.showColorPickerComponent = false
        this.showNinjaReactionTimerComponent = false
        this.showCountdownTimerComponent = false
        this.showRandomNamePickerComponent = false
        this.flexBox = ''
        this.qrGen = 'active'
        this.passGen = ''
        this.colPicker = ''
        this.countTimer = ''
        this.namePicker = ''
        this.ninjaGame = ''

      },
      showPasswordGenerator(){
        this.showAboutComponent = false
        this.showFlexboxComponent = false
        this.showQrCodeGeneratorComponent = false
        this.showPasswordGeneratorComponent = true
        this.showColorPickerComponent = false
        this.showNinjaReactionTimerComponent = false
        this.showCountdownTimerComponent = false
        this.showRandomNamePickerComponent = false
        this.flexBox = ''
        this.qrGen = ''
        this.colPicker = ''
        this.passGen = 'active'
        this.countTimer = ''
        this.namePicker = ''
        this.ninjaGame = ''

      },
      showCountdownTimer(){
        this.showAboutComponent = false
        this.showFlexboxComponent = false
        this.showQrCodeGeneratorComponent = false
        this.showPasswordGeneratorComponent = false
        this.showColorPickerComponent = false
        this.showNinjaReactionTimerComponent = false
        this.showCountdownTimerComponent = true
        this.showRandomNamePickerComponent = false
        this.flexBox = ''
        this.qrGen = ''
        this.passGen = ''
        this.colPicker = ''
        this.countTimer = 'active'
        this.namePicker = ''
        this.ninjaGame = ''
      },
      showNinjaReactionTimer(){
        this.showAboutComponent = false
        this.showFlexboxComponent = false
        this.showQrCodeGeneratorComponent = false
        this.showPasswordGeneratorComponent = false
        this.showColorPickerComponent = false
        this.showNinjaReactionTimerComponent = true
        this.showCountdownTimerComponent = false
        this.showRandomNamePickerComponent = false
        this.flexBox = ''
        this.qrGen = ''
        this.passGen = ''
        this.colPicker = ''
        this.countTimer = ''
        this.namePicker = ''
        this.ninjaGame = 'active'
      },
      showColorPicker(){
        this.showAboutComponent = false
        this.showFlexboxComponent = false
        this.showQrCodeGeneratorComponent = false
        this.showPasswordGeneratorComponent = false
        this.showColorPickerComponent = true
        this.showNinjaReactionTimerComponent = false
        this.showCountdownTimerComponent = false
        this.showRandomNamePickerComponent = false
        this.flexBox = ''
        this.qrGen = ''
        this.passGen = ''
        this.colPicker = 'active'
        this.countTimer = ''
        this.namePicker = ''
        this.ninjaGame = ''
      },
      showRandomNamePicker(){
        this.showAboutComponent = false
        this.showFlexboxComponent = false
        this.showQrCodeGeneratorComponent = false
        this.showPasswordGeneratorComponent = false
        this.showColorPickerComponent = false
        this.showNinjaReactionTimerComponent = false
        this.showCountdownTimerComponent = false
        this.showRandomNamePickerComponent = true
        this.flexBox = ''
        this.qrGen = ''
        this.passGen = ''
        this.colPicker = ''
        this.countTimer = ''
        this.namePicker = 'active'
        this.ninjaGame = ''
      }
      
    }
  }
</script>

<style>
  div .active{
    background-color: #2c3f50;
    cursor: pointer;
  }
  div .active a{
    color: aliceblue;
  }
  div a{
    color: #2c3f50;
  }
</style>