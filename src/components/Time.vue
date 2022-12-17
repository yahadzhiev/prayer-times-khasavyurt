<template>
  <div class="time" :class="[time, { active: isActiveTime }, { next: isNextTime }]">
  <table class="table-m">
  <tbody>
  <tr>
	<td class="table-tdL">
    <div class="time-body">
    <h4 class="time-body-title">
     {{ $t(`times.${time}`) }}
    </h4>
    <Timer v-if="isActiveTime" :timer="timer" />
    </div>
  </td>
	<td class="table-tdC">
    <h3 class="time-body-value">
    {{ datetime.format('HH:mm') }}
    </h3>
  </td>
	<td class="table-tdR">
   На арабском!
  </td>
  </tr>
  </tbody>
  </table>
</template>

<script>
import Timer from './Timer'

export default {
  name: 'Time',
  components: {
    Timer
  },
  props: {
    time: String,
    datetime: Object,
    currentTime: String,
    timer: String,
    nextTime: String
  },
  computed: {
    isActiveTime() {
      return this.time === this.currentTime
    },
    isNextTime() {
      return this.time === this.nextTime
    }
  }
}
</script>

<style>
.time {
  position: relative;
  min-height: 90px;
  display: flex;
  align-items: center;
  padding: 10px 30px;
  transition-delay: 0.1s;

  &.active &-body,
  &.next &-body {
    font-size: 2.2em;
  }

  &-body {
    &-title {
      font-weight: normal;
    }

    &-value {
      margin-top: 6px;
      font-size: 2.3em;
    }
  }
}

;

.table-m {
  width: 100%;
  table-layout: fixed;
}

.table-m tr {
  white-space: pre-wrap;
}

.table-tdL {
  text-align: left
}

.table-tdC {
  text-align: center
}

.table-tdR {
  text-align: right
}

.mobile-table {
  width: 100%;
  max-width: 100%;
}
</style>
