<template lang='pug'>
span.timepiece.countdown
  span(v-if='distance !== null && distance <= 0 && expiredText') {{ expiredText }}
  template(v-else-if='distance')
    span.days {{ displayDays }}
    span.daysSeparator(v-if='daysSeparator' v-html='daysSeparator')
    span.hours {{ displayHours }}
    span.hoursSeparator(v-if='hoursSeparator' v-html='hoursSeparator')
    span.minutes {{ displayMinutes }}
    span.minutesSeparator(v-if='minutesSeparator' v-html='minutesSeparator')
    span.seconds {{ displaySeconds }}
    span.secondsSeparator(v-if='secondsSeparator' v-html='secondsSeparator')
</template>

<script>
export default {
  props: {
    // date='2050-03-14'
    date: {
      required: true
    },
    // expiredText='Expired'
    expiredText: {
      type: String
    },
    // :leadingZeroes='true'
    // :leadingZeroes='{ hours: true, minutes: true, seconds: true }'
    leadingZeroes: {
      type: [Boolean, Object],
      default: false
    },
    daysSeparator: {
      type: String,
      default: '&nbsp;days '
    },
    hoursSeparator: {
      type: String,
      default: '&nbsp;hours '
    },
    minutesSeparator: {
      type: String,
      default: '&nbsp;minutes '
    },
    secondsSeparator: {
      type: String,
      default: '&nbsp;seconds'
    }
  },

  data () {
    return {
      distance: null,
      displayDays: '',
      displayHours: '',
      displayMinutes: '',
      displaySeconds: ''
    }
  },

  created () {
    var self = this
    // Set the date we're counting down to
    var countDownDate = new Date(self.date).getTime()
    var x = setInterval(function() {
      // Get today's date and time
      var now = new Date().getTime()

      // Find the distance between now and the count down date
      self.distance = countDownDate - now

      // Time calculations for days, hours, minutes and seconds
      var days = Math.floor(self.distance / (1000 * 60 * 60 * 24))
      var hours = Math.floor((self.distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60))
      var minutes = Math.floor((self.distance % (1000 * 60 * 60)) / (1000 * 60))
      var seconds = Math.floor((self.distance % (1000 * 60)) / 1000)

      // Set displayText to hold the result
      self.displayDays = days
      self.displayHours = (((self.leadingZeroes === true || self.leadingZeroes['hours']) && hours < 10) ? '0' : '') + hours
      self.displayMinutes = (((self.leadingZeroes === true || self.leadingZeroes['minutes']) && minutes < 10) ? '0' : '') + minutes
      self.displaySeconds = (((self.leadingZeroes === true || self.leadingZeroes['seconds']) && seconds < 10) ? '0' : '') + seconds

      // Text to show if the countdown is finished
      if (self.distance < 0) {
        clearInterval(x)
      }
    }, 1000)
  }
}
</script>
