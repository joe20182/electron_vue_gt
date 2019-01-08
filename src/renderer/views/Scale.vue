<template>
    <div class="scale-wrapper">
        <h1>Guitar fretboard for noobs</h1>
        <div class="neck">
            <ul class="string hE">
                <li v-for="i in length + 1" :key="i"><span>{{cvtName(i + baseNotes[0] - 1)}}</span></li>
            </ul>
            <ul class="string B">
                <li v-for="i in length + 1" :key="i"><span>{{cvtName(i + baseNotes[1] - 1)}}</span></li>
            </ul>
            <ul class="string G">
                <li v-for="i in length + 1" :key="i"><span>{{cvtName(i + baseNotes[2] - 1)}}</span></li>
            </ul>
            <ul class="string D">
                <li v-for="i in length + 1" :key="i"><span>{{cvtName(i + baseNotes[3] - 1)}}</span></li>
            </ul>
            <ul class="string A">
                <li v-for="i in length + 1" :key="i"><span>{{cvtName(i + baseNotes[4] - 1)}}</span></li>
            </ul>
            <ul class="string lE">
                <li v-for="i in length + 1" :key="i"><span>{{cvtName(i + baseNotes[5] - 1)}}</span></li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Scale',
    data() {
        return {
            key: null,
            baseNotes: [4, 11, 7, 2, 9, 4],
            length: 24
        }
    },
    methods: {
        cvtName(num) {
            // 音名轉換
            switch (num % 12) {
            case 0:
                return 'C';
                break;
            case 1:
                return '#C';
                break;
            case 2:
                return 'D';
                break;
            case 3:
                return '#D';
                break;
            case 4:
                return 'E';
                break;
            case 5:
                return 'F';
                break;
            case 6:
                return '#F';
                break;
            case 7:
                return 'G';
                break;
            case 8:
                return '#G';
                break;
            case 9:
                return 'A';
                break;
            case 10:
                return '#A';
                break;
            case 11:
                return 'B';
                break;
            }
        }
    }
}
</script>

<style lang="scss">
@import '../../styles/mixins.scss';
.scale-wrapper {
    font-size: 18px;
    .neck {
        position: relative;
        background-image: linear-gradient(45deg, #826132, #946b30);
        ul {
            list-style: none;
            @include clearfix();
            color: #FFF;
            font-weight: bold;
            position: relative;
            text-align: center;
            text-shadow: 1px 1px 0px #000;
            height: 32px;
            overflow: hidden;
            li {
                float: left;
                border-right: 3px solid #CCC;
                width: 50px;
                height: 32px;
                line-height: 32px;
                &:first-child {
                    width: 26px;
                    background-color: #1D1B1B;
                    border-right: 2px solid #666;
                    box-shadow: 2px 0px 0px rgba(black, .4);
                }
            }
            &:before {
                content: '';
                display: block;
                position: absolute;
                left: 26px;
                width: calc(100% - 26px);
            }
            &.hE {
                &:before {
                    top: 16px;
                    height: 1px;
                    background-color: #CCC;
                }
            }
            &.B {
                &:before {
                    top: 16px;
                    height: 1px;
                    background-color: #CCC;
                }
            }
            &.G {
                &:before {
                    top: 15px;
                    height: 2px;
                    background-color: rgba(#CCC, .6);
                }
            }
            &.D {
                &:before {
                    top: 15px;
                    height: 2px;
                    background-color: rgba(#CCC, .6);
                }
            }
            &.A {
                &:before {
                    top: 15px;
                    height: 3px;
                    background-color: rgba(#EEE, .5);
                }
            }
            &.lE {
                &:before {
                    top: 15px;
                    height: 3px;
                    background-color: rgba(#EEE, .5);
                }
            }
        }
    }
}
</style>
