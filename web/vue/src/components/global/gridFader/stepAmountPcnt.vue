<template>
  <vue-slider v-model="value" @change="valueChange" :tooltip='hover' :marks="marks" :max=50 :min=0 :interval=0.1 direction="btt" :height="150"/>
</template>
 
<script>
import VueSlider from 'vue-slider-component'
import 'vue-slider-component/theme/antd.css'
 
export default {
  model: {
    prop: 'value',
    event: 'change'
  },
  props: {
    value: Number
  },
  components: {
    VueSlider
  },
  data: function() {
    return {
    	value: this.value,
      marks: [0, 10, 20, 30, 40, 50],
    } 
  },
  methods: {
      valueChange(value) {
        this.$emit('changeStepAmountPcnt', value);
      }
    }
}
</script>