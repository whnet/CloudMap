<template>
    <div class="content-wrap">
        <span class="close-btn" title="关闭" @click="close">&times;</span>
        <info-list :list="environmentalList" cMenu="环保信息"  :currentTitle="cItem" @getList="chageList"></info-list>
        <div class="table-wrap">
            <router-view></router-view>
        </div>
        <div class="download-wrap">
            <span class="download-icon"></span>
            <span class="download">下载企业报告</span>
        </div>
    </div>
</template>

<script type="es6">
    import infoList from '@/components/info-list'
    export default{
        name:'environmental',
        props:['cItem'],
        data(){
            return{
                environmentalList:['环保行政处罚','国家重点监控企业名单','环境问题督办通知','“12369”环保举报热线案件情况','重点环境案件处理情况']
            }
        },
        methods:{
            close(){
                this.$emit('close')
            },
            chageList(txt){
                txt = txt[0];
                switch (txt){
                    case '环保行政处罚':
                        this.$router.push({name:'environmentalDetails'});
                        break;
                    case '国家重点监控企业名单':
                        this.$router.push({name:'companiesList'});
                        break;
                    case '环境问题督办通知':
                        this.$router.push({name:'overseeNoticeList'});
                        break;
                    case '“12369”环保举报热线案件情况':
                        this.$router.push({name:'hotlineSituationList'});
                        break;
                    case '重点环境案件处理情况':
                        this.$router.push({name:'processingSituationList'});
                        break;
                }
            }
        },
        components:{
            infoList
        }
    }

</script>
<style scoped>
    .content-wrap{
        position: absolute;
        top: 120px;
        right: 0;
        bottom:0;
        left: 0;
        margin: auto;
        width: 60%;
        height: 700px;
        padding: 0 50px;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        align-items: stretch;
        background: url("../../../static/img/table-bg.png") center no-repeat;
        background-size: 100% 100%;
    }
    .content-wrap .table-wrap{
        box-sizing: border-box;
        flex: auto;
        padding-top: 20px;
        display: flex;
        justify-content: center;
        align-items: stretch;
        /*overflow: auto;*/
        overflow-x: hidden;
        padding-right: 5px;
    }
    /*.content-wrap .table-wrap:hover::-webkit-scrollbar-thumb{*/
        /*background:rgba(7,100,180,1)*/
    /*}*/
    .content-wrap .close-btn{
        position: absolute;
        top: 20px;
        right: 20px;
        display: flex;
        justify-content: center;
        width: 20px;
        height: 20px;
        line-height: 15px;
        border: none;
        color: #0a6cbb;
        font-size: 40px;
        cursor: pointer;
        transition: all .5s;
    }
    .content-wrap .close-btn:hover{
        color: #1e96f6;
    }
    .vScrollbar{
        flex: auto;
    }
    .content-wrap .download-wrap{
        height: 90px;
        flex: none;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }
    .content-wrap .download-wrap span{
        color: #fff;
    }
    .download-wrap .download-icon{
        margin-bottom: 5px;
        width: 19px;
        height: 19px;
        background: url("../../../static/img/download-icon.png") center no-repeat;
    }
    .download-wrap .download{
        font-size: 14px;
        font-weight: bold;
        border-bottom: 1px solid #fff;
        cursor: pointer;
    }
    .download-wrap .download:hover{
        color: #068bb0;
        border-bottom-color: #068bb0;
    }
</style>