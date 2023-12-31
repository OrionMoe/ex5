<template>
    <div
        style="
            text-align: center;
            height: 100%;
            padding: 20px 0 0 0;
            margin: 0px;
        "
    >
        <div class="welcome">
            <b>
                <span> 欢迎使用仓库管理系统，</span>
                <span style="color: black">
                    {{ user.name }}
                </span>
            </b>
        </div>

        <br />
        <br />
        <h5 style="font-size: 26px">
            <span style="color: grey; font-size: 22px">你已经登入：</span>
            {{
                user.roleId == 0
                    ? "超级管理员"
                    : user.roleId == 1
                    ? "管理员"
                    : "用户"
            }}
        </h5>
        <DateUtils></DateUtils>

    </div>
</template>

<script>
import DateUtils from './DateUtils.vue';
export default {
    name: "Home",
    components: { DateUtils },
    data() {
        return {
            user: {},
        };
    },
    computed: {},
    methods: {
        init() {
            this.user = JSON.parse(sessionStorage.getItem("CurUser"));
        },
    },
    created() {
        this.init();
    },
};
</script>

<style scoped>
.welcome {
    font-size: 30px; 
    color: grey;
}
</style>