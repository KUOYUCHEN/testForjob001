<!-- @format -->

<script setup lang="ts">
import { ref } from "vue";
const lists = ref([
    { id: 1, name: "白頭翁的特性", isfoucs: true },
    { id: 2, name: "白頭翁的故事", isfoucs: false },
    { id: 3, name: "白頭翁的美照", isfoucs: false },
    { id: 4, name: "白頭翁的危機", isfoucs: false },
]);
const describes = ref([
    {
        id: 1,
        text: "白頭鵯體長約17到22公分，額至頭頂純黑色而富有光澤，兩眼上方至後枕白色，形成一白色枕環。耳羽後部有一白斑，此白環與白斑在黑色的頭部均極為醒目，老鳥的枕羽(後頭部)更潔白，所以又叫「白頭翁」。",
        name: "外觀",
    },
    {
        id: 2,
        text: "白頭翁和麻雀、綠繡眼合稱「城市三寶」，常成群出現在平原區灌木叢、丘陵樹林地帶，以及校園、公園、庭院、行道中的各種高高的電線與樹上。",
        name: "棲地",
    },
    {
        id: 3,
        text: "以果樹的漿果和種子為主食，並時常飛入果園偷吃果實，還會吃嫩葉嫩芽，尤其是胡蝶蘭的嫩葉嫩芽葉，偶爾啄食昆蟲。",
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
                <div>白頭翁不吃小米</div>
                <div class="logoWrap">
                    <div class="container1">
                        <div class="scale-wrapper">
                            <div class="blackbird-logo"></div>
                        </div>
                    </div>
                </div>
            </span>
            <div class="lists" v-for="list in lists" :key="list.id">
                <span
                    :class="{ focus: list.isfoucs }"
                    @click="clickList(list.id)"
                >
                    {{ list.name }}
                </span>
            </div>
        </div>
        <div class="content">
            <div class="picture">
                <div class="picContent">
                    <div class="picTitle">白頭翁 (Chinese bulbul)</div>
                    <span class="picText"
                        >又名白頭鵯。以果實、昆蟲為主食，無法消化小米、穀類。平均壽命約
                        8~10 年。</span
                    >
                </div>
                <img src="../assets/img001.svg" alt="" />
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
                    <p>
                        {{ describe.text }}
                    </p>
                </div>
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped>
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
            margin-bottom: 21.74px;
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
                bottom: 36.85px;
                right: 44.75px;
                color: #fff;
                .picTitle {
                    font-weight: 700;
                    font-size: 48px;
                    text-align: right;
                    line-height: 48px;
                    margin-bottom: 4px;
                }
                .picText {
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
                    width: 200px;
                    font-weight: 400;
                    font-size: 16px;
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

.container1 {
    position: absolute;
    top: 25px;
    left: 18px;
    width: 60px;
    height: 60px;
}

.scale-wrapper {
    transform: scale(0.14);
    transform-origin: top left;
}
</style>
