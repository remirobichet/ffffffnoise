<template>
  <div class="container">
    <button>ffffffnoise</button>
  </div>
</template>

<script>
import * as Tone from 'tone'
export default {
  // https://tonejs.github.io/docs/r13/Noise
  mounted () {
    const noise = new Tone.Noise('pink').start()
    const autoFilter = new Tone.AutoFilter({
      frequency: '8m',
      min: 800,
      max: 15000
    }).connect(Tone.Master)

    // connect the noise
    noise.connect(autoFilter)
    // start the autofilter LFO
    autoFilter.start()
  }
}
</script>

<style>
</style>
