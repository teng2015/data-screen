<template>
    <div id="app">
        <div class="header">
            <h1>工业大数据可视化分析平台</h1>
        </div>
        <div class="content">
            <div class="left">
                <bubble-chart></bubble-chart>
                <area-stack></area-stack>
                <line-chart></line-chart>
            </div>
            <div class="middle">
                <machines-pannel></machines-pannel>
            </div>
            <!--<div class="right">-->
            <!--<map-chart></map-chart>-->
            <!--<heatmap-chart></heatmap-chart>-->
            <!--</div>-->
            <div class="right">
                <corona-chart></corona-chart>
                <nightingale-rose-chart></nightingale-rose-chart>
            </div>
        </div>
        <transition name="fade">
            <router-view></router-view>
        </transition>
    </div>
</template>

<script>
import { mapState } from 'vuex'
import bubbleChart from './components/bubble-chart'
import areaStack from './components/area-stack'
import nightingaleRoseChart from './components/nightingale-rose-chart'
import coronaChart from './components/corona-chart'
import lineChart from './components/line-chart'
import machinesPannel from './views/machines-pannel/index'
import machineDetail from './views/machine-detail'

export default {
    name: 'app',
    components: {
        bubbleChart,
        areaStack,
        nightingaleRoseChart,
        coronaChart,
        lineChart,
        machinesPannel,
        machineDetail
    },
    computed: {
        ...mapState(['machineDetailShow'])
    }
}
</script>

<style lang="less" rel="stylesheet/less">
@import './style/colors.less';
#app {
    font-family: -apple-system, BlinkMacSystemFont, "PingFang SC", "Helvetica Neue", STHeiti, "Microsoft Yahei", Tahoma, Simsun, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    /*color: #2c3e50;*/
    background: url("./assets/bg.jpg") fixed;
    min-height: 100%;
    display: flex;
    flex-direction: column;
    .header {
        color: #fff;
        padding-top: 20px;
        text-align: center;
        text-shadow: 0 0 20px @DEFAULT;
    }
    .content {
        display: flex;
        flex-direction: row;
        .left {
            padding: 10px;
        }

        .middle {
            flex-grow: 1;
        }
        .right {
            display: flex;
            flex-direction: column;
            /*align-items:flex-end;*/
        }
    }
}

.fade-enter-active,
.fade-leave-active {
    transition: opacity .3s
}

.fade-enter,
.fade-leave-active {
    opacity: 0
}
</style>
