<template>
  <label for="inp" class="inp">
    <input
      @change="$emit('customChange', $event.target.value)"
      :type="type"
      class="inp"
      placeholder="&nbsp;"
    />
    <span class="label">{{ input }}</span>
    <span class="focus-bg"></span>
  </label>
</template>

<script>
export default {
  name: "Input",
  props: {
    input: String,
    type: String,
  },
};
</script>

<style scoped>
.inp {
  position: relative;
  width: 100%;
  max-width: 280px;
  border-radius: 3px;
  overflow: hidden;
}
.inp .label {
  position: absolute;
  top: 20px;
  left: 12px;
  font-size: 14px;
  color: rgb(0, 0, 0);
  font-weight: 500;
  transform-origin: 0 0;
  transform: translate3d(0, 0, 0);
  transition: all 0.2s ease;
  pointer-events: none;
}
.inp .focus-bg {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(248, 2, 2, 0);
  z-index: -1;
  transform: scaleX(0);
  transform-origin: left;
}
.inp input {
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
  width: 100%;
  border: 0;
  font-family: inherit;
  padding: 16px 12px 0 12px;
  height: 56px;
  font-size: 16px;
  font-weight: 400;
  background: rgba(0, 0, 0, 0);
  box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.3);
  color: white;
  transition: all 0.15s ease;
}
.inp input:hover {
  background: rgba(255, 0, 0, 0.04);
  box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.5);
}
.inp input:not(:-moz-placeholder-shown) + .label {
  color: rgb(255, 255, 255);
  transform: translate3d(0, -12px, 0) scale(0.75);
}
.inp input:not(:-ms-input-placeholder) + .label {
  color: rgb(255, 255, 255);
  transform: translate3d(0, -12px, 0) scale(0.75);
}
.inp input:not(:placeholder-shown) + .label {
  color: rgb(255, 255, 255);
  transform: translate3d(0, -12px, 0) scale(0.75);
}
.inp input:focus {
  background: rgba(255, 3, 3, 0.05);
  outline: none;
  box-shadow: inset 0 -2px 0 #0077ff;
}
.inp input:focus + .label {
  color: white;
  transform: translate3d(0, -12px, 0) scale(0.75);
}
.inp input:focus + .label + .focus-bg {
  transform: scaleX(1);
  transition: all 0.1s ease;
}
</style>
