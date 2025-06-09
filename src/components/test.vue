<!-- @format -->

<script setup lang="ts">
import { ref } from "vue";
// mob選單控制
const menuToggle = ref(false);
const lists = ref([
    { id: 1, name: "白頭翁的特性", isfoucs: true },
    { id: 2, name: "白頭翁的故事", isfoucs: false },
    { id: 3, name: "白頭翁的美照", isfoucs: false },
    { id: 4, name: "白頭翁的危機", isfoucs: false },
]);
const wrapPunctuationWithSub = (text: string) => {
    return text.replace(/([，。！？、；：])/g, "<sub>$1</sub>");
};
const describes = ref([
    {
        id: 1,
        text: wrapPunctuationWithSub(
            "白頭鵯體長約17到22公分，額至頭頂純黑色而富有光　澤，兩眼上方至後枕白色，形成一白色枕環。耳羽後部有一白斑，此白環與白斑在黑色的頭部均極為醒目，老鳥的枕羽(後頭部)更潔白，所以又叫「白頭翁」。"
        ),
        mobText: wrapPunctuationWithSub(
            "白頭鵯體長約17到22公分，額至頭頂純黑色而富有光澤，兩眼上方至後枕白色，形成一白色枕環。耳羽後部有一白斑，此白環與白斑在黑色的頭部均極為醒目，老鳥的枕羽(後頭部)更潔白，所以又叫「白頭翁」。"
        ),
        name: "外觀",
    },
    {
        id: 2,
        text: wrapPunctuationWithSub(
            "白頭翁和麻雀、綠繡眼合　稱「城市三寶」，常成群出現在平原區灌木叢、丘陵樹林地帶，以及校園、公園、庭院、行道中的各種高高的電線與樹上。"
        ),
        mobText: wrapPunctuationWithSub(
            "白頭翁和麻雀、綠繡眼合稱「城市三寶」，常成群出現在平原區灌木叢、丘陵樹林地帶，以及校園、公園、庭院、行道中的各種高高的電線與樹　上。"
        ),
        name: "棲地",
    },
    {
        id: 3,
        text: wrapPunctuationWithSub(
            "以果樹的漿果和種子為主　食，並時常飛入果園偷吃果實，還會吃嫩葉嫩芽，尤其是胡蝶蘭的嫩葉嫩芽葉，偶爾啄食昆蟲。"
        ),
        mobText: wrapPunctuationWithSub(
            "以果樹的漿果和種子為主食，並時常飛入果園偷吃果實，還會吃嫩葉嫩芽，尤其是胡蝶蘭的嫩葉嫩芽葉，偶爾啄食昆　蟲。"
        ),
        name: "食性",
    },
]);

const clickList = (id: number) => {
    lists.value.forEach((list) => {
        list.isfoucs = list.id === id;
    });
};
</script>
<template>
    <div class="wrap">
        <div class="sidebar">
            <span class="title">
                <div class="burger-icon" @click="menuToggle = !menuToggle">
                    <template v-if="!menuToggle">
                        <span class="line line1"></span>
                        <span class="line line2"></span>
                        <span class="line line3"></span>
                    </template>
                    <template v-else>
                        <img src="../assets/cancel.svg" alt="cancel" />
                    </template>
                </div>
                <div class="titleName">白頭翁不吃小米</div>
                <div class="logoWrap">
                    <div class="container">
                        <div class="scale-wrapper">
                            <div class="blackbird-logo"></div>
                        </div>
                    </div>
                </div>
            </span>
            <div class="lists pc" v-for="list in lists" :key="list.id">
                <span
                    :class="{ focus: list.isfoucs }"
                    @click="clickList(list.id)"
                >
                    {{ list.name }}
                </span>
            </div>

            <template v-if="menuToggle">
                <div class="lists mob" v-for="list in lists" :key="list.id">
                    <span
                        :class="{ focus: list.isfoucs }"
                        @click="clickList(list.id)"
                    >
                        {{ list.name }}
                    </span>
                </div>
            </template>
        </div>
        <div class="content">
            <div class="picture">
                <div class="picContent">
                    <div class="picTitle">白頭翁 (Chinese bulbul)</div>
                    <span class="picText"
                        >又名白頭鵯<sub>。</sub>以果實<sub>、</sub>昆蟲為主食<sub>，</sub>無法消化小米<sub>、</sub>穀類<sub>。</sub>平均壽命約
                        8~10 年<sub>。</sub></span
                    >
                </div>
                <img src="https://i.ibb.co/7dDqfvZn/img001.png" alt="" />
            </div>
            <div class="description">
                <div
                    class="describes"
                    v-for="describe in describes"
                    :key="describe.id"
                >
                    <div class="describTitle">
                        <div class="point"></div>
                        {{ describe.name }}
                    </div>
                    <p class="pc" v-html="describe.text"></p>
                    <p class="mob" v-html="describe.mobText"></p>
                </div>
            </div>
        </div>
    </div>
</template>

<style lang="scss">
.wrap {
    display: flex;
    width: 100%;
    height: 100vh;
    .sidebar {
        width: 345px;
        background-color: #f0f0f0;
        text-align: center;
        .title {
            display: inline-block;
            font-weight: 700;
            font-size: 30px;
            margin-top: 78.33px;
            margin-bottom: 75.67px;
            position: relative;
            .titleName {
                font-weight: 700;
            }
            .burger-icon {
                position: absolute;
                left: 18px;
                bottom: 30px;
                width: 24px;
                height: 24px;
                display: flex;
                flex-direction: column;
                justify-content: center;
                gap: 6px;
                align-items: flex-start;
                .line {
                    height: 6px;
                    background-color: black;
                    border-radius: 2px;
                    display: block;
                }
                /* 三條線寬度不同 */
                .line1 {
                    width: 90%;
                }
                .line2 {
                    width: 60%;
                }
                .line3 {
                    width: 100%;
                }
            }

            .logoWrap {
                background-color: #fff;
                position: absolute;
                width: 100px;
                height: 100px;
                border-radius: 50%;
                box-shadow: 0px 0px 3px rgba(0, 0, 0, 0.5);
                display: flex;
                justify-content: center;
                text-align: center;
                bottom: -50%;
                right: -57%;
                z-index: 1;
            }
        }
        .lists {
            cursor: pointer;
            font-size: 18px;
            margin-bottom: 17.53px;
        }
    }
    .content {
        width: calc(100% - 345px);
        display: flex;
        flex-direction: column;
        height: 100vh;
        .picture {
            position: relative;
            .picContent {
                position: absolute;
                left: 36px;
                right: 36px;
                bottom: 36px;
                color: #fff;
                .picTitle {
                    font-weight: 700;
                    font-size: 48px;
                    text-align: right;
                    line-height: 48px;
                    margin-bottom: 16px;
                }
                .picText {
                    display: block;
                    text-align: right;
                    font-weight: 400;
                    line-height: 16px;
                }
            }
            width: 100%;
            height: 60%;
            img {
                width: 100%;
                height: 100%;
                object-fit: cover;
            }
        }
        .description {
            padding: 0px 50px;
            background-color: #dcccbc;
            display: flex;
            justify-content: space-around;
            align-items: center;
            height: 40%;
            overflow: auto;
            .describes {
                font-size: 16px;
                display: flex;
                height: 225px;
                .describTitle {
                    width: 36px;
                    font-weight: 700;
                    font-size: 36px;
                    margin-right: 37.84px;
                    position: relative;
                    height: 80px;
                    line-height: 1.1;
                    .point {
                        width: 24px;
                        height: 24px;
                        background-color: rgba(#a65c5c, 0.7);
                        border-radius: 50%;
                        position: absolute;
                        bottom: -9px;
                        right: -15px;
                    }
                    .point::after {
                        content: "";
                        position: absolute;
                        top: 50%;
                        left: 50%;
                        width: 8px;
                        height: 8px;
                        background-color: rgba(#dcccbc, 1);
                        border-radius: 50%;
                        transform: translate(-50%, -50%);
                    }
                }
                p {
                    &.mob {
                        display: none;
                    }
                    width: 200px;
                    font-weight: 400;
                    font-size: 16px;
                    letter-spacing: normal;
                    line-height: 1.4;
                }
            }
        }
    }
}

.focus {
    color: #aa6666;
    font-size: 18px;
    text-decoration: underline;
    text-underline-offset: 4px;
    font-weight: 700;
}

.container {
    position: absolute;
    top: 25px;
    left: 18px;
    width: 60px;
    height: 60px;
}

.scale-wrapper {
    transform: scale(0.14);
    transform-origin: top left;
    .blackbird-logo {
        width: 13em;
        height: 12em;
    }
}

/* 手機寬度 */
@media (max-width: 375px) {
    .wrap {
        // display: none;
        flex-wrap: wrap;
        .sidebar {
            background-color: #fff;
            width: 100%;
            display: flex;
            justify-content: center;
            text-align: center;
            flex-wrap: wrap;
            z-index: 1;
            .title {
                background-color: #fff;
                margin-top: 0px;
                // margin: auto;
                margin-bottom: 0px;
                font-size: 24px;
                width: 100%;
                height: 88px;
                display: inline-flex;
                .titleName {
                    margin: auto;
                }
                .logoWrap {
                    // display: none;
                    width: 50px;
                    height: 50px;
                    right: 18px;
                    bottom: 20px;
                    .container {
                        position: absolute;
                        top: 12px;
                        left: 11px;
                        width: 60px;
                        height: 60px;
                        .scale-wrapper {
                            transform: scale(0.08);
                            transform-origin: top left;
                        }
                    }
                }
            }
            .lists {
                &.pc {
                    display: none;
                }
                width: 100%;
                padding-bottom: 0px;
                background-color: #fff;
            }
        }
        .content {
            width: 100%;
            height: calc(100vh - 88px);
            .picture {
                .picContent {
                    left: 36px;
                    right: 36px;
                    bottom: 17px;
                    .picTitle {
                        margin-bottom: 9px;
                    }
                }
                height: 50%;
                img {
                    object-fit: cover;
                }
            }
            .description {
                height: 50%;
                height: unset;
                padding: 50.5px 36.38px;
                flex-direction: column;
                align-items: center;
                .describes {
                    width: 100%;
                    margin-bottom: 50.5px;
                    .describTitle {
                        margin-right: 20px;
                        .point {
                            bottom: -10px;
                        }
                    }
                    p {
                        &.pc {
                            display: none;
                        }
                        &.mob {
                            display: block;
                        }
                        width: auto;
                        letter-spacing: 0.12em;
                    }
                }
                :last-child {
                    margin-bottom: 0px;
                }
            }
        }
    }
}

@media (min-width: 375px) {
    .wrap {
        .sidebar {
            content {
                .description {
                    &.pc {
                        display: block;
                    }
                }
            }
            .lists {
                &.mob {
                    display: none;
                }
            }
            .title {
                .burger-icon {
                    display: none;
                }
            }
        }
    }
}

sub {
    font-size: 16px;
    transform: translate(-5px, 2px);
    display: inline-block;
}
</style>
