<template>
  <div class="takino-container">
    <div v-show="position" class="takinao" :class="[position]">
      <h3>takinão pop up</h3>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      position: '',
      beforeLastPosition: 0,
      lastPosition: 0
    }
  },

  methods: {
    takinoLoop () {
      let position

      do {
        position = Math.floor(Math.random() * 4 + 1)
      } while (position === this.lastPosition || position === this.beforeLastPosition)

      switch (position) {
        case 1: 
          this.position = 'top'
          break;
        case 2: 
          this.position = 'right'
          break;
        case 3: 
          this.position = 'bottom'
          break;
        case 4: 
          this.position = 'left'
          break;
      }
      console.log(position, 'before:',this.beforeLastPosition, 'last', this.lastPosition)
      this.beforeLastPosition = this.lastPosition
      this.lastPosition = position
    }
  },

  created() {
    setInterval(this.takinoLoop, 1000)
  }
}
</script>

<style>
.takinao{
  position: absolute;
}

.top {
  left: 70%;
  transform: rotate(180deg);
}
.right {
  right: 0;
  bottom: 30%;
  transform: rotate(-90deg) translateY(240%);
}
.bottom {
  right: 80%;
  bottom: 0;
}
.left {
  bottom: 80%;
  transform: rotate(90deg) translateY(240%);
}
</style>