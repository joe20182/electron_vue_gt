<template>
    <div class="scale-wrapper">
        <h1>Guitar fretboard for begineers</h1>
        <div class="options">
            <span class="title">Fret</span>
            <div class="option" :class="{'active': length === 22}" @click="changeFret(22)">22</div>
            <div class="option" :class="{'active': length === 24}" @click="changeFret(24)">24</div>
        </div>
        <div class="options">
            <span class="title">Key</span>
            <div class="option" :class="{'active': key === item}" v-for="(item, i) in keyMap" :key="i" @click="changeKey(item)">{{item}}</div>
        </div>
        <div class="neck">
            <ul class="string hE">
                <li v-for="i in length + 1" :key="i" :class="{'rootNote': isRootNote(i + baseNotes[0] - 1)}">
                    <span v-show="isInKey(i + baseNotes[0] - 1)">{{cvtName(i + baseNotes[0] - 1)}}</span>
                </li>
            </ul>
            <ul class="string B">
                <li v-for="i in length + 1" :key="i" :class="{'rootNote': isRootNote(i + baseNotes[1] - 1)}">
                    <span v-show="isInKey(i + baseNotes[1] - 1)">{{cvtName(i + baseNotes[1] - 1)}}</span>
                </li>
            </ul>
            <ul class="string G">
                <li v-for="i in length + 1" :key="i" :class="{'rootNote': isRootNote(i + baseNotes[2] - 1)}">
                    <span v-show="isInKey(i + baseNotes[2] - 1)">{{cvtName(i + baseNotes[2] - 1)}}</span>
                </li>
            </ul>
            <ul class="string D">
                <li v-for="i in length + 1" :key="i" :class="{'rootNote': isRootNote(i + baseNotes[3] - 1)}">
                    <span v-show="isInKey(i + baseNotes[3] - 1)">{{cvtName(i + baseNotes[3] - 1)}}</span>
                </li>
            </ul>
            <ul class="string A">
                <li v-for="i in length + 1" :key="i" :class="{'rootNote': isRootNote(i + baseNotes[4] - 1)}">
                    <span v-show="isInKey(i + baseNotes[4] - 1)">{{cvtName(i + baseNotes[4] - 1)}}</span>
                </li>
            </ul>
            <ul class="string lE">
                <li v-for="i in length + 1" :key="i" :class="{'rootNote': isRootNote(i + baseNotes[5] - 1)}">
                    <span v-show="isInKey(i + baseNotes[5] - 1)">{{cvtName(i + baseNotes[5] - 1)}}</span>
                </li>
            </ul>
            <div class="dot dot1"></div>
            <div class="dot dot2"></div>
            <div class="dot dot3"></div>
            <div class="dot dot4"></div>
            <div class="dot dot5"></div>
            <div class="dot dot6"></div>
            <div class="dot dot7"></div>
            <div class="dot dot8"></div>
            <div class="dot dot9"></div>
            <div class="dot dot10"></div>
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
            length: 22,
            keyMap: ['C', '#C', 'D', '#D', 'E', 'F', '#F', 'G', '#G', 'A', '#A', 'B']
        }
    },
    methods: {
        cvtName(num) {
            // 音名轉換
            return this.keyMap[num % 12];
        },
        changeKey(key) {
            if (key === this.key) {
                this.key = null;
            } else {
                this.key = key;
            }
        },
        changeFret(num) {
            this.length = num;
        },
        isInKey(num) {
            // 算出調內音
            if (!this.key) {
                return true;
            }
            switch (Math.abs(num - this.keyMap.indexOf(this.key)) % 12) {
            case 0:
            case 2:
            case 4:
            case 5:
            case 7:
            case 9:
            case 11:
                return true;
                break;
            default:
                return false;
                break;
            }
        },
        isRootNote(num) {
            if (!this.key) {
                return false;
            } else {
                return (num - this.keyMap.indexOf(this.key)) % 12 === 0;
            }
        }
    }
}
</script>

<style lang="scss">
@import '../../styles/mixins.scss';
$d: #1D1B1B;
.scale-wrapper {
    font-size: 18px;
    padding: 15px;
    max-width: 1300px;
    margin: 0 auto;
    .neck {
        position: relative;
        background-image: linear-gradient(45deg, #826132, #987D55);
        overflow: hidden;
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
                position: relative;
                &:first-child {
                    width: 26px;
                    background-color: $d;
                    border-right: 2px solid #666;
                    box-shadow: 2px 0px 0px rgba(black, .4);
                }
                &.rootNote {
                    color: #f00;
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
        .dot {
            position: absolute;
            width: 20px;
            height: 20px;
            border-radius: 50%;
            background-color: #1D1B1B;
            opacity: .6;
            &.dot1 {
                top: 85px;
                left: 140px;
            }
            &.dot2 {
                top: 85px;
                left: 240px;
            }
            &.dot3 {
                top: 85px;
                left: 340px;
            }
            &.dot4 {
                top: 85px;
                left: 440px;
            }
            &.dot5 {
                top: 54px;
                left: 590px;
            }
            &.dot6 {
                top: 119px;
                left: 590px;
            }
            &.dot7 {
                top: 85px;
                left: 740px;
            }
            &.dot8 {
                top: 85px;
                left: 840px;
            }
            &.dot9 {
                top: 85px;
                left: 940px;
            }
            &.dot10 {
                top: 85px;
                left: 1040px;
            }
        }
    }
    h1 {
        margin-bottom: 20px;
    }
    .options {
        font-weight: bold;
        margin-bottom: 12px;
        display: flex;
        align-items: center;
        .title {
            display: inline-block;
            width: 42px;
        }
        .option {
            display: inline-block;
            font-weight: 400;
            cursor: pointer;
            min-width: 40px;
            text-align: center;
            margin-left: 10px;
            border: 1px solid $d;
            box-sizing: border-box;
            transition: .5s;
            position: relative;
            overflow: hidden;
            &:after {
                content: '';
                display: block;
                width: 100%;
                height: 100%;
                background-color: $d;
                position: absolute;
                top: 0;
                left: -100%;
                transition: .5s;
                z-index: -1;
            }
            &:hover,
            &.active {
                color: #FFF;
                &:after {
                    left: 0;
                }
            }
        }
    }
}
</style>
