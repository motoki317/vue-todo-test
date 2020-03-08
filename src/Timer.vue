<template>
  <div>
    <h2>タイマー</h2>
    <p>10秒で止めるやつ</p>
    <div>{{ timerMessage }}</div>
    <div>
      <button v-bind:disabled="state !== 0" @click="timerStart()">
        スタート
      </button>
      <button v-bind:disabled="state !== 1" @click="timerStop()">
        ストップ
      </button>
      <button v-bind:disabled="state !== 2" @click="timerReset()">
        リセット
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "timer",
  data() {
    return {
      timerMessage: "00.000 s",
      date: Date.now(),
      state: 0
    };
  },
  methods: {
    timerStart: function() {
      this.date = Date.now();
      this.timerMessage = "計測中...";
      this.state = 1;
    },
    timerStop: function() {
      const millis = Date.now() - this.date;
      this.timerMessage = millis / 1000 + " s " + this.getMessage(millis);
      this.state = 2;
    },
    getMessage: function(millis) {
      if (millis < 9000) {
        return "早すぎ";
      } else if (9900 < millis && millis < 10100) {
        return "プロ";
      } else if (millis < 11000) {
        return "惜しい";
      } else {
        return "遅すぎ";
      }
    },
    timerReset: function() {
      this.timerMessage = "00.000 s";
      this.state = 0;
    }
  }
};
</script>
