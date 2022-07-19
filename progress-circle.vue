<template>
    <div class="progress-circle">
        <svg :width="size" :height="size" viewBox="0 0 100 100">
            <circle r="50"  cx="50" cy="50" fill="transparent" class="progress-background"></circle>
            <circle r="50" cx="50" cy="50" fill="transparent" class="progress-bar" :stroke-dasharray="dashArray" :stroke-dashoffset="dashOffset"></circle>
        </svg>
        <div class="percent-text" :style="{'font-size': fontSize}">{{percent}}%</div>
    </div>
</template>

<script>
export default {
    props: {
        size: {
            type: Number,
            default: 100
        },
        percent: {
            type: Number,
            default: 0
        },
        fontSize: {
            type: String,
            default: '24px'
        }
    },
    data () {
          return {
            //    总长度
            dashArray: Math.PI * 2 * 50
          }
    },
    computed: {
        dashOffset () {
            return (1 - this.percent * 0.01) * this.dashArray
        }
    }
}
</script>

<style>
.progress-circle {
    position: absolute;
    top: -2px;
    left: -2px;
}
circle {
    stroke-width: 10px;
    transform-origin: center;
}
.progress-background{
    stroke: transparent;
    transform:scale(0.9);
}
.progress-bar{
    stroke:var(--primary-color);
    transform: rotate(-90deg) scale(0.9);
}
.percent-text {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}
</style>
