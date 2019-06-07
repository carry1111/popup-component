<template>
    <div class="content">
        <input type="button" value="弹弹" @click="popup">
        <div class="popup" v-show=isShow @click="hide">
            <div class="center" ref="center" @click.stop="stop">
                <input type="tel" class="keyboard" maxlength="4" autocomplete="off" v-model="value">
                <ul class="nav">
                    <li>{{valueArr[0]}}</li>
                    <li>{{valueArr[1]}}</li>
                    <li>{{valueArr[2]}}</li>
                    <li>{{valueArr[3]}}</li>
                </ul>
            </div>
        </div>
    </div>
</template>
<script>
export default{
    data(){
        return {
            isShow: false,
            value: '',
        }
    },
    computed: {
        valueArr() {
            return this.value.split('');
        } 
    },
    methods: {
        popup(){
            this.isShow = !this.isShow;
        },
        hide(e){
            // if(e.target != this.$refs.center){
                this.isShow = false;
            // }
        },
        stop(){

        },
        keyup(){

        }
    }
}
</script>
<style lang="scss" scoped>
    ul{
        margin: 0;
        padding: 0;
        list-style-type: none;
    }
    .popup{
        position: fixed;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        background-color: rgba(0,0,0,.5);
    }
    .center{
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%,-50%);
        width: 280px;
        height: 290px;
        background-color: #fff;
        .keyboard{
            position: absolute;
            left: 30px;
            top: 10px;
            width: 200px;
            height: 40px;
            opacity: 0;
        }
        .nav{
            display: flex;
            justify-content: center;
            margin-top: 10px;
            li{
                // flex: 1;
                width: 40px;
                height: 40px;
                line-height: 40px;
                margin-right: 10px;
                border: 1px solid #ccc;
            }
        }
    }
    
</style>