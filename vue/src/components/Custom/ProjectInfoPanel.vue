<template>
    <div class="projectInfo">
        <div class="infoLeft">
            <p class="textBold">PROJEKT:</p>
            <p class="pName">{{selectedProject.name}}</p>
            <p class="levelDown"> > </p>
            <p class="textBold" v-if="currentSprint !== null">TRENUTNI SPRINT:</p>
            <p class="pName" v-if="currentSprint !== null">{{currentSprint.name}}</p>
            <p class="sDate" v-if="currentSprint !== null">({{startDateFormat}} - {{endDateFormat}})</p>
            <p v-if="currentSprint === null" class="sConfirmation">no active sprint</p>
        </div>
        <div class="infoRight">
            <p class="textBold">UPORABNIŠKA VLOGA:</p>
            <p class="roleName">{{userProjectRole}}</p>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'ProjectInfoPanel',
        props: {
            selectedProject: Object,
            currentSprint: Object,
            userProjectRole: String
        },
        methods: {
        },
        computed: {
            startDateFormat: function () {
                return new Date(this.currentSprint.startDate * 1000).toString().substr(0, 10);
            },
            endDateFormat: function () {
                return new Date(this.currentSprint.endDate * 1000).toString().substr(0, 10);
            }

        }
    }
</script>

<style scoped>
    .projectInfo {
        display: flex;
        justify-content: space-between;
        padding: 10px 20px;
        background-color: #F6F6F7;
        border-bottom: 2px solid white;
    }

    .infoLeft {
        display: flex;
        padding: 10px;
        align-items: center;
    }

    .infoRight {
        display: flex;
        padding: 10px;
        border: 1px solid #3093A0;
        border-radius: 8px;
        background-color: white;
    }

    .textBold {
        font-weight: bold;
        font-size: 16px;
        padding-right: 10px;
        color: #969DAA;
    }

    #infoLeft .textBold {
        font-size: 16px;

    }

    .pName {
        font-size: 16px;
    }

    .roleName {
        font-size: 16px;
    }

    .levelDown {
        padding: 0 15px;
        font-weight: bolder;
        color: #969DAA;
    }

    .sDate {
        color: #969DAA;
        padding: 0 10px;
        font-style: italic;
    }

    .sConfirmation {
        color: #969DAA;
        font-style: italic;
    }
</style>