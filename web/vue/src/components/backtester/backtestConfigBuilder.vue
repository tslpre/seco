<template lang='pug'>
  div
    strat-picker.my2(v-on:stratConfig='updateStrat').contain
    paper-trader(v-on:settings='updatePaperTrader').contain
    dataset-picker.my2(v-on:dataset='updateDataset').contain
</template>

<script>

import datasetPicker from '../global/configbuilder/datasetpicker.vue'
import stratPicker from '../global/configbuilder/stratpicker.vue'
import paperTrader from '../global/configbuilder/papertrader.vue'
import _ from 'lodash'
import { get } from '../../tools/ajax'

export default {
  created: function() {
    get('configPart/performanceAnalyzer', (error, response) => {
      this.performanceAnalyzer = toml.parse(response.part);
      this.performanceAnalyzer.enabled = true;
    });
  },
  data: () => {
    return {
      dataset: {},
      strat: {},
      paperTrader: {},
      performanceAnalyzer: {}
    }
  },
  components: {
    stratPicker,
    datasetPicker,
    paperTrader
  },
  computed: {
    market: function() {
      if(!this.dataset.exchange)
        return {};

      return {
        exchange: this.dataset.exchange,
        currency: this.dataset.currency,
        asset: this.dataset.asset
      }
    },
    range: function() {
      if(!this.dataset.exchange)
        return {};

      return {
        from: this.dataset.from,
        to: this.dataset.to
      }
    },
    config: function() {
      let config = {};
      Object.assign(
        config,
        { watch: this.market },
        { paperTrader: this.paperTrader },
        this.strat,
        {
          backtest: {
            daterange: this.range
          },
          backtestResultExporter: {
            enabled: true,
            writeToDisk: false,
            data: {
              stratUpdates: false,
              roundtrips: true,
              stratCandles: true,
              stratCandleProps: ['open', 'high', 'low', 'close', 'vwp', 'volume', 'trades'],
              trades: true,
              markers: true
            }
          }
        },
        { performanceAnalyzer: this.performanceAnalyzer },
      );

      config.valid = this.validConfig(config);
      config.backtestResultExporter.enabled = true;

      return config;
    }
  },
  methods: {
    validConfig: function(config) {
      if(!config.backtest)
        return false;

      if(!config.backtest.daterange)
        return false;

      if(_.isEmpty(config.backtest.daterange))
        return false;

      if(!config.watch)
        return false;

      if(!config.tradingAdvisor)
        return false;

      let strat = config.tradingAdvisor.method;
      if(_.isEmpty(config[ strat ]))
        return false;

      if(config.tradingAdvisor) {
        if(_.isNaN(config.tradingAdvisor.candleSize))
          return false;
        else if(config.tradingAdvisor.candleSize == 0)
          return false;
      }

      return true;
    },
    updateDataset: function(set) {
      console.log('updateDataset: dataset and config in builder');
      console.log(set);
      console.log(this.config);
      this.dataset = set;
      this.$emit('config', this.config);
    },
    updateStrat: function(sc) {
      this.strat = sc;
      this.$emit('config', this.config);
    },
    updatePaperTrader: function(pt) {
      this.paperTrader = pt;
      this.paperTrader.enabled = true;
      this.$emit('config', this.config);
    },
  }
}
</script>

<style>
</style>
