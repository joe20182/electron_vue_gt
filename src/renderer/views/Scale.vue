<template>
    <div class="scale-wrapper">
        <h1>Guitar fretboard for noobs</h1>
        <div class="options">
            <span class="title">Fret</span>
            <div class="option" :class="{'active': length === 22}" @click="changeFret(22)">22</div>
            <div class="option" :class="{'active': length === 24}" @click="changeFret(24)">24</div>
        </div>
        <div class="options">
            <span class="title">Key</span>
            <div class="option">C</div>
            <div class="option">#C</div>
            <div class="option">D</div>
            <div class="option">#D</div>
            <div class="option">E</div>
            <div class="option">F</div>
            <div class="option">#F</div>
            <div class="option">G</div>
            <div class="option">#G</div>
            <div class="option">A</div>
            <div class="option">#A</div>
            <div class="option">B</div>
        </div>
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
            length: 22
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
        },
        changeKey() {
            // 1
        },
        changeFret(num) {
            this.length = num;
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
    .neck {
        position: relative;
        background-image: linear-gradient(45deg, #826132, #987D55);
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
                    background-color: $d;
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
