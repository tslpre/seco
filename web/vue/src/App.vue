<script>

import top from './components/layout/header.vue'
import modal from './components/layout/modal.vue'

export default {
  name: 'app',
  components: {
    top,
    modal
  }
}
</script>

<template lang='pug'>
  #app
    top
    .fill
      router-view.view
    modal
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Barlow+Condensed:wght@600&display=swap');
#app {
  display: flex;
  min-height: 100vh;
  flex-direction: column;
}

.fill {
  flex: 1;
}
.text {
  max-width: 500px;
}
body {
    line-height: 1;
}
input {
    background: none;
    margin-top: .1em;
}
input, textarea {
    padding: .3rem;
    margin-bottom: .1rem;
    display: block;
    width: 100%;
    box-shadow: none;
    border: thin solid rgba(216,216,216,.99);
}
input[type="checkbox"] {
    float:left;
    margin-right: 0px;
    display: inline !important;
    padding: 0;
    margin: 0;
    display: block;
    width: 10px;
    -webkit-box-shadow: none;
    box-shadow: none;
    border: thin solid hsla(0,0%,85%,.99);
    width: 20px;
    height: 20px;
}
div.input-checkbox strong {
  padding-left: 8px;
}
.h1, .h2, .h3, .h4, h1, h2, h3, h4 {
    margin: -0.114rem 0 .5rem;
    font-weight: inherit;
    line-height: 1.42;
}
h4 {
    margin: 0 0 .5rem;
    font-weight: inherit;
    line-height: 1;
}

h5 {
    margin-bottom: 0;
    margin-top: 20px;
    font-family: "Arial Narrow",sans-serif;
    font-weight: lighter;
    font-size: 1em;
}
.params {
    min-height: 124px;
    line-height: 1.3em;
}

.hr {
  margin-top: 2rem;
  margin-bottom: 2rem;
  height: 10px;
  background-color: rgba(250,250,250,.99);
}

.contain {
  width: 1100px;
  margin-left: auto;
  margin-right: auto;
}
.btn--primary-m:active,
.btn--primary-m:focus,
.btn--primary-m {
  display: inline-block;
  margin-right: 8px;
    margin-top: 0px;
    margin-bottom: 8px;
  height: 24px;
  padding: 0 14px;
   border-radius: 16px;
   font-size: 14px;
   color: #000;
  font-weight: bold;
  background-color:#ffffff;
  text-shadow: 0 1px 3px rgb(36 180 126 / 40%);
  -webkit-box-shadow: 31px 24px 40px rgb(50 50 50 / 47%), 0px 0px 34px rgb(0 0 0 / 0%);
  box-shadow: 31px 24px 40px rgb(50 50 50 / 47%), 0px 0px 34px rgb(0 0 0 / 0%);
  text-decoration: none;
  line-height: 22px;
  transition: transform 300ms;
  -webkit-transition: -webkit-transform .3s;
  transition: -webkit-transform .3s;
  transition: transform .3s,-webkit-transform .3s;
}

.btn--primary-m:hover
 {
  background-color:#000;
  color: #ffffff;
  text-decoration: none;
  box-shadow: 31px 24px 27px rgb(30 30 30 / 47%), 0px 0px 34px rgb(0 0 0 / 0%);
}


.btn--primary {
  display: inline-block;
  margin-right: 8px;
    margin-top: 0px;
    margin-bottom: 8px;
  height: 27px;
  padding: 0 14px;
   border-radius: 16px;
   font-size: 14px;
  background-color: #126fad;
  text-shadow: 0 0px 0px rgb(36 180 126 / 0%);
  -webkit-box-shadow: 0px 0px 0px rgb(50 50 50 / 0%), 0 0px 0px rgb(0 0 0 / 0%);
  box-shadow: 0px 0px 0px rgb(50 50 50 / 0%), 0 0px 0px rgb(0 0 0 / 0%);
  color: #fff;
  text-decoration: none;
  line-height: 27px;
  transition: transform 100ms;
  -webkit-transition: -webkit-transform .1s;
  transition: -webkit-transform .1s;
  transition: transform .1s,-webkit-transform .1s;
}
.btn--primary:focus,
.btn--primary:hover {
  background-color: #5eb9f5;
  color: #fff;
  text-decoration: none;
}

.btn--primary:active {
  transform: translateY(1px);
  -webkit-box-shadow: 0px 0px 0px rgb(50 50 50 / 20%), 0 3px 6px rgb(0 0 0 / 4%);
  box-shadow: 0px 0px 0px rgb(50 50 50 / 20%), 0 3px 6px rgb(0 0 0 / 4%);
}
td a.w100--s.btn--primary {
    padding: 0 8px;
    margin: 0;
    line-height: 1;
    height: 10px;
    font-size: 10px;
    background-color: #ffffff;
    color: #000000;
}
.btn--red {
    border-color: #e43525;
    background-color: #e74c3c;
    color: #fff;
}
.btn, .btn--blue, .btn--gray, .btn--green, .btn--link, .btn--red {
    padding: 0rem 1rem;
    border: 0;
    color: #fff;
    text-decoration: none;
    text-align: center;
    line-height: 30px;
}
.btn, .btn--blue, .btn--gray, .btn--green, .btn--link, .btn--red {
    border-radius: 10px;
}

.m1 {
    margin: 0.1rem;
}
.my2 {
    margin-top: 0;
    margin-bottom: 0;
}
/* Label styles: style as needed */
label {
  display:block;
  margin-top:0.2em;
  font-size: 0.9em;
  color:#777;
}

/* Container used for styling the custom select, the buttom class adds the bg gradient, corners, etc. */
.custom-select {
  position: relative;
  display:block;
  margin-top:0.1em;
  padding:0;
}

/* This is the native select, we're making everything but the text invisible so we can see the button styles in the wrapper */
.custom-select select {
  width:100%;
  margin:0;
  background:none;
  border: 1px solid transparent;
  outline: none;
  /* Prefixed box-sizing rules necessary for older browsers */
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
  /* Remove select styling */
  appearance: none;
  -webkit-appearance: none;
  /* Magic font size number to prevent iOS text zoom */
  font-size:16px;
  /* General select styles: change as needed */
  font-family: helvetica, sans-serif;
  font-weight: bold;
  color: #444;
  /*padding: .6em 1.9em .5em .8em;*/
  padding: 0.2em 0.6em .1em .4em;
  line-height:1.3;
}

.vue-slider-dot-handle {
    margin-left: -9px;
    width: 230%;
    border-radius: 27%;
    background-color: #fff;
    border: 2px solid #9cd5ff;
}

.vue-slider {
    margin-top: 10px;
}

.vue-slider-btt .vue-slider-mark-label, .vue-slider-ttb .vue-slider-mark-label {
    left: 100%;
    margin-left: 18px;
    border-left-style: none;
    background-image: url('../public/static/mark.png');
    background-repeat: no-repeat;
    background-position-y: 6px;
    background-position-x: -4px;
    padding-left: 15px;
}
.vue-slider-btt .vue-slider-mark-step {
    background: transparent;
    /* border: none; */
    top: 0;
}
.vue-slider-mark-step {
    width: 100%;
    height: 100%;
    border-radius: 50%;
    -webkit-box-shadow: 0 0 0 0px #e8e8e8;
    box-shadow: 0 0 0 0px #e8e8e8;
    background-color: #fff;
}
.vue-slider-process {
    background-color: #000;
    border-radius: 15px;
    -webkit-transition: background-color .3s;
    transition: background-color .3s;
}
.vue-slider-rail {
    background-color: #000;
    border-radius: 15px;
    -webkit-transition: background-color .3s;
    transition: background-color .3s;
}
.vue-slider-dot-handle {
    margin-left: -9px;
    width: 230%;
    border-radius: 27%;
    background-color: #fff;
    border: 2px solid #000;
}
.vue-slider.vue-slider-ltr {
    margin-top: 15px;
}
.vue-slider-ltr .vue-slider-mark {
    -webkit-transform: translate(-50%,-50%);
    transform: translate(-50%,-50%);
}
.vue-slider-ltr .vue-slider-dot-handle {
  width: 100%;
}

.vue-slider-dot-handle:hover, .vue-slider:hover .vue-slider-dot-handle-focus, .vue-slider:hover .vue-slider-dot-handle:hover {
    border-color: #000;
    background:#000;
}
.vue-slider:hover .vue-slider-rail {
    background-color: #000;
}
.vue-slider:hover .vue-slider-process {
    background-color: #000;
}
.vue-slider:hover .vue-slider-mark-step-active {
    -webkit-box-shadow: 0 0 0 0px #69c0ff;
    box-shadow: 0 0 0 0px #69c0ff;
}
.vue-slider-mark-step {
    width: 100%;
    height: 100%;
    border-radius: 50%;
    -webkit-box-shadow: 0 0 0 0 #000;
    box-shadow: 0 0 0 0 #000;
    background-color: #000;
}
.vue-slider-ltr .vue-slider-mark-label, .vue-slider-rtl .vue-slider-mark-label {
    top: 100%;
    margin-top: 10px;
}
.input-checkbox {
    height: 24px;
}
.dancer {
  background-image: url('../public/static/dancer.gif');
  background-repeat: no-repeat;
  background-size: 380px;
  background-position: 34px 108px;
}

.dancer-orders {
  background-image: url('../public/static/dancer.gif');
  background-repeat: no-repeat;
  background-size: 280px;
  background-position: right bottom;
}
.dancer-candles {
  background-image: url('../public/static/dancer.gif');
  background-repeat: no-repeat;
  background-size: 220px;
  background-position: right bottom;
}
div.right-panel-col {
  padding-top: 14px;
}
div.dashboard-params {
  margin-bottom: 12px;
}
div.dashboard-ctrl {
  padding-bottom: 12px;
}
div.dashboard-ctrl-labels {
  padding-bottom: 1px;
}
div.dashboard-ctrl-params {
  margin-top: 12px;
}
.dashboard-ctrl-params p {
  margin: 0;
  font-size: 0.8rem;
}
.dashboard-params p,
.dashboard-ctrl-labels p {
  margin: 0;
  font-size: 0.7rem;
  padding-right: 4px;
}
.dashboard-params h3,
.dashboard-ctrl-labels h3 {
  line-height: 1;
  margin: 0;
  padding: 0;
  font-size: 1.5rem;
  font-family: 'Barlow Condensed';
}
.dashboard-params h2,
.dashboard-ctrl-labels h2 {
  line-height: 1;
  margin: 0;
  padding: 0;
  font-size: 1.8rem;
  font-family: 'Barlow Condensed';
}
.dashboard-params h1,
.dashboard-ctrl-labels h1 {
  line-height: 1;
  margin: 0;
  padding: 0;
  font-size: 3.8rem;
  font-family: 'Barlow Condensed';
}
.knob-param {
  position: relative;
}
.knob-param h3 {
  position: absolute;
  top: 37px;
    left: 37px;
    text-align: center;
    font-size: 1.4em;
    width: 27px;
  font-family: 'Barlow Condensed';
}
</style>
