<template lang='pug'>
  .contain.roundtrips
    table(v-if='roundtrips.length')
      thead
        tr
          th Entry at (UTC)
          th Exit at (UTC)
          th Exposure
          th Entry balance
          th Exit balance
          th P&amp;L
          th Profit
        tr(v-for='rt in roundtrips')
          td {{ fmt(rt.entryAt) }}
          td {{ fmt(rt.exitAt) }}
          td {{ diff(rt.duration) }}
          td {{ round(rt.entryBalance) }}
          td {{ round(rt.exitBalance) }}
          template(v-if="Math.sign(rt.pnl)===-1")
            td.loss {{ Math.sign(rt.pnl)*rt.pnl.toFixed(2) }}
            td.loss {{ rt.profit.toFixed(2) }}%
          template(v-else)
            td.profit {{ rt.pnl.toFixed(2) }}
            td.profit {{ rt.profit.toFixed(2) }}%
    div(v-if='!roundtrips.length')
      p Not enough data to display
</template>

<script>
import _ from 'lodash'

export default {
  props: ['roundtrips'],
  data: () => {
    return {}
  },
  methods: {
    diff: n => moment.duration(n).humanize(),
    humanizeDuration: (n) => window.humanizeDuration(n),
    fmt: date => {

      // roundtrips coming out of a backtest
      // are unix timestamp, live roundtrips
      // are date strings.
      // TODO: normalize

      let mom;

      if(_.isNumber(date)) {
        mom = moment.unix(date);
      } else {
        mom = moment(date).utc();
      }

      return mom.utc().format('YYYY-MM-DD HH:mm');
    },
    fmt: mom => moment(mom * 1000).utc().format('YYYY-MM-DD HH:mm'),
    round: n => (+n).toFixed(3),
  },
}
</script>

<style>

.roundtrips {
  margin-top: 50px;
  margin-bottom: 50px;
}

.roundtrips table {
  width: 100%;
}

.roundtrips table th,
.roundtrips table td {
  border: 1px solid #c6cbd1;
  padding: 8px 12px;
}

.roundtrips table td.loss {
  color: red;
  text-align: right;
}
.roundtrips table td.profit {
  color: #30b74a;
  text-align: right;
}

.roundtrips table tr:nth-child(2n) {
  background-color: #f6f8fa;
}

</style>
