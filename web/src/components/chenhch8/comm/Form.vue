<template>
<div class="grade-form">
  <div class="grade-border border-horizontal" :style="othClass"></div>
  <div class="grade-border border-horizontal" :style="othClass"></div>
  <div class="grade-border border-vertical" :style="othClass"></div>
  <div class="grade-border border-vertical" :style="othClass"></div>
  <p :style="othClass">{{ msg }}</p>
</div>
</template>

<script>
export default {
  props: [ 'msg', 'addClass', 'active' ],
  data() {
    return {
      othClass: {}
    }
  },
  created: function() {
    this.setActive()
  },
  watch: {
    active: function() {
      this.setActive();
    }
  },
  methods: {
    setActive() {
      if (this.active)
        this.othClass = this.addClass
      else
        this.othClass = {}
    }
  }
}
</script>

<style>
.grade-form {
  position: relative;
  width: calc(100% - 2vw);
  border: 0;
  height: auto;
  margin: 2vh auto 4vh auto;
}
.grade-border {
  position: absolute;
  border: 1px solid #8a683a;
}
.border-horizontal {
  width: 1vw;
  height: 100%;
}
.border-horizontal:nth-child(1) {
  left: -1vw;
  border-right: 0;
}
.border-horizontal:nth-child(2) {
  right: -1vw;
  border-left: 0;
}
.border-vertical {
  width: 100%;
  height: 1vw;
}
.border-vertical:nth-child(3) {
  top: -1vw;
  border-bottom: 0;
}
.border-vertical:nth-child(4) {
  bottom: -1vw;
  border-top: 0;
}
.grade-form p {
  margin: 0;
  color: #906e5e;
}
</style>