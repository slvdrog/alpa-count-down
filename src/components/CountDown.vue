<template>
  <div id="clock">
    <h1>
      <div>
        <span> {{ hours }} :</span>
        <span> {{ minutes }} :</span>
        <span> {{ seconds }} :</span>
        <span> {{ milliseconds }} </span>
      </div>
      <p class="share">
        <a :href="timerString" data-action="share/whatsapp/share"><i class='fa fa-whatsapp'/></a>
      </p>
    </h1>
  </div>
</template>

<script>

import countdown from 'countdown'
import 'font-awesome/css/font-awesome.css'

countdown.DEFAULTS =
  countdown.HOURS |
  countdown.MINUTES |
  countdown.SECONDS |
  countdown.MILLISECONDS

export default {
  name: 'CountDown',
  data () {
    return {
      hours: '',
      minutes: '',
      seconds: '',
      milliseconds: '',
      timerString: ''
    }
  },
  mounted () {
    setInterval(this.updateTime, 1)
  },
  methods: {
    updateTime () {
      let timer = countdown(new Date('2017-12-15T15:00:00-0300'), null, countdown.DEFAULTS)

      var string = 'Alpa in ' + timer.toString()
      this.timerString = 'whatsapp://send?text=' + string
      this.hours = timer.hours
      this.minutes = this.zeroPadding(timer.minutes, 2)
      this.seconds = this.zeroPadding(timer.seconds, 2)
      this.milliseconds = this.zeroPadding(timer.milliseconds, 4)
    },
    zeroPadding (num, digit) {
      var zero = ''
      for (var i = 0; i < digit; i++) {
        zero += '0'
      }
      return (zero + num).slice(-digit)
    }
  }
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
html,body {
    height: 100%;
}
body {
    background: #0f3854;
    background: radial-gradient(ellipse at center,  #0a2e38  0%, #000000 70%);
    background-size: 100%;
}
p {
    margin: 0;
    padding: 0;
}
#clock {
    font-family: 'Share Tech Mono', monospace;
    color: #ffffff;
    text-align: center;
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    color: #daf6ff;
    text-shadow: 0 0 20px rgba(10, 175, 0, 1),  0 0 20px rgba(10, 175, 0, 0);
    width: 100%;
    font-size: 3vw;
    padding-top: 100px;
}

@media screen and (min-width: 601px) {
	.share {
    font-size: 100px;
    padding-top: 5vh;
  }
}
@media screen and (max-width: 600px) {
	.share { font-size: 30px }
}
.fa {
  color: rgba(10, 175, 0, 1);
}
</style>