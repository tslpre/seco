<template lang='pug'>
  div
    div.contain
      .grd
        .grd-row
          .grd-row-col-3-6.px1
            h4.contain Backtest
          .grd-row-col-3-6.px1
            a.w100--s.my1.btn--primary(href='#', v-if='backtestState !== "fetching"', v-on:click.prevent='run') Backtest
    div(v-if='backtestable')
      .txt--center
        div(v-if='backtestState === "fetching"').scan-btn
          p Running backtest..
          spinner
    result(v-if='backtestResult && backtestState === "fetched"', :result='backtestResult')
    config-builder(v-on:config='check')
    
    
</template>

<script>
import configBuilder from './backtestConfigBuilder.vue'
import result from './result/result.vue'
import { post } from '../../tools/ajax'
import spinner from '../global/blockSpinner.vue'

export default {
  data: () => {
    return {
      backtestable: false,
      backtestState: 'idle',
      backtestResult: false,
      config: false,
    }
  },
  methods: {
    check: function(config) {
      // console.log('CHECK', config);
      this.config = config;

      if(!config.valid)
        return this.backtestable = false;

      this.backtestable = true;
    },
    run: function() {
      this.backtestState = 'fetching';

      post('backtest', this.config, (error, response) => {
        this.backtestState = 'fetched';
        this.backtestResult = response;
      });
    }
  },
  components: {
    configBuilder,
    result,
    spinner
  }
}
</script>
