<template>
    <div class="container score-container">
        <div class="zan-panel">
            <div class="zan-cell zan-field">
                <div class="zan-cell__hd zan-field__title">姓名</div>
                <input class="zan-field__input zan-cell__bd" type="text" placeholder="请输入姓名" v-model="name" />
                <div class="zan-cell__ft" />
            </div>
            <div class="zan-cell zan-field">
                <div class="zan-cell__hd zan-field__title">考号</div>
                <input class="zan-field__input zan-cell__bd" type="number" placeholder="请输入学号" v-model="id" />
                <div class="zan-cell__ft" />
            </div>
            <div class="zan-cell zan-field">
                <div class="zan-cell__hd zan-field__title">验证码</div>
                <input class="zan-field__input zan-cell__bd" type="text" placeholder="请输入验证码" v-model="proof" />
                <img class="proof" :src="proofUrl" @click="refreshProofUrl" />
                <div class="zan-cell__ft" />
            </div>
        </div>
        <Button :disabled="!(name && id && proof)" @click="query" />
        <div class="list" v-if="visible.list">
            <div class="zan-cell" v-for="item in list" :key="item.index">
                <div class="icon zan-cell__icon zan-icon zan-icon-description" />
                <div class="zan-cell__bd">{{item.subject}}</div>
                <div class="zan-cell__ft">{{item.score}}</div>
            </div>
        </div>
    </div>
</template>

<script>
    import Button from '@/components/Button';

    export default {
        components: { Button },
        data() {
            return {
                name: '',
                id: '',
                proof: '',
                proofUrl: '',
                visible: { list: false },
                list: [],
            };
        },
        methods: {
            refreshProofUrl() {},
            query() {
                wx.showModal({
                    title: '提示',
                    content: '暂未开放！',
                    showCancel: false,
                });
            },
        },
    };
</script>

<style lang="less">
    .list {
        width: 100%;
        margin-top: 20px;
        .zan-cell {
            .icon {
                color: #29BB73;
                font-size: 18px;
                margin-right: 20px;
            }
            height: 20px;
            background: #FFFFFF;
        }
    }
</style>
