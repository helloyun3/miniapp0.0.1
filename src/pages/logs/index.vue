<template>
  <div>
    <map
  id="map"
  longitude="113.324520"
  latitude="23.099994"
  scale="14"
  :controls="controls"
  @controltap="controltap"
  :markers="markers"
  @markertap="markertap"
  :polyline="polyline"
  @regionchange="regionchange"
  show-location
  style="width: 100%; height: 100vh;"
></map>
  </div>
</template>

<script>

export default {
  components: {
  },

  data () {
    return {
      markers: [{
      iconPath: '/static/images/others.png',
      id: 0,
      latitude: 30.571331,
      longitude: 114.347997,
      width: 50,
      height: 50
    }],
    polyline: [{
      points: [{
        longitude: 113.3245211,
        latitude: 23.10229
      }, {
        longitude: 113.324520,
        latitude: 23.21229
      }, {
        longitude: 113.324520,
        latitude: 23.21229
      }],
      color: '#FF0000DD',
      width: 2,
      dottedLine: true
    }],
    controls:[]
    }
  },
    methods: {
          regionchange(e) {
            console.log(e.type)
          },
          markertap(event) {
            console.log(event)
          },
          controltap(e) {
            console.log(e.controlId)
          }
      },
  created () {
  }

}
</script>
<style>
body,html{height:100%}
</style>
