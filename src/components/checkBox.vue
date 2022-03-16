<template>
    <div>
        <div v-if="division==='radio'">
            <radio name="radio" :checked="ckList[0].isCheked" @click="onchange(0,'ck1')">라디오1</radio>
            <radio name="radio" :checked="ckList[1].isCheked" @click="onchange(1,'ck1')">라디오2</radio>
            <radio name="radio" :checked="ckList[2].isCheked" @click="onchange(2,'ck1')">라디오3</radio>
            <radio name="radio" :checked="ckList[3].isCheked" @click="onchange(3,'ck1')">라디오4</radio>
        </div>
        <div v-if="division==='checkbox'">

            <check-box v-model="ckList[0].isCheked" :disabled="disCk" @change="onchange(0,'ck1')"><span>체크박스1</span></check-box>
            <check-box v-model="ckList[1].isCheked" :disabled="disCk" @change="onchange(1,'ck2')"><span>체크박스2</span></check-box>
            <check-box v-model="ckList[2].isCheked" :disabled="disCk" @change="onchange(2,'ck3')"><span>체크박스3</span></check-box>
            <check-box v-model="ckList[3].isCheked" :disabled="disCk" @change="onchange(3,'ck4')"><span>체크박스4</span></check-box>
        </div>
        <!-- 선택시 안내 -->
        <div>
            <table>
                <tr>
                    <th v-if="isShowCk1">선택 안내1</th>
                    <ul v-if="ckData1==='ck1'">1번이 선택 되었습니다</ul>
                    <li>1번 선택확인</li>
                                        <ul v-if="ckData1==='ck2'">2번이 선택 되었습니다</ul>
                    <li>2번 선택확인</li>
                                        <ul v-if="ckData1==='ck3'">3번이 선택 되었습니다</ul>
                    <li>3번 선택확인</li>
                                        <ul v-if="ckData1==='ck4'">4번이 선택 되었습니다</ul>
                    <li>4번 선택확인</li>
                                       <th v-if="isShowCk2">선택 안내2</th>
                    <ul v-if="ckData2==='ck1'">1번이 선택 되었습니다</ul>
                    <li>1번 선택확인</li>
                                        <ul v-if="ckData2==='ck2'">2번이 선택 되었습니다</ul>
                    <li>2번 선택확인</li>
                                        <ul v-if="ckData2==='ck3'">3번이 선택 되었습니다</ul>
                    <li>3번 선택확인</li>
                                        <ul v-if="ckData2==='ck4'">4번이 선택 되었습니다</ul>
                    <li>4번 선택확인</li>
                </tr>
            </table>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            ckList:[
                {
                isCheked:false,
                data:'ck1'
                },
                                {
                isCheked:false,
                data:'ck2'
                },                {
                isCheked:false,
                data:'ck3'
                },                {
                isCheked:false,
                data:'ck4'
                },
            ],
            disCk:false,
            checkType : 0,
            checkData :'',
            division : '',
            isShowCk1 : false,
            isShowCk2 : false,
            count:0,
            ckData1:'',
            ckData2:''
        }
        
    },
    fetch(){
        //초기세팅 설정
        //라디오, 체크박스 구분
        // this.division = this.$route.params.division
        this.division = 'checkBox'
        

        //vue null체크방법 확인하기   
    },
    methods: {
        onchange(type, data){
            console.log('타입종류 구분(one, two)', type)
            //한가지만 선택가능 , radio일때
            if(this.division == 'radio'){
                this.ckData1 = type
                this.isShowCk1 = true
                return
            }

            //두가지 선택가능, checkBox일때
            if(this.division == 'checkBox'){
                this.count=0
                for(let i=0 ; this.ckList.length ; i++){
                    if(this.ckList[i].isCheked){
                        this.count++
                        if(this.count===1){
                            this.ckData1 = this.ckList[i].data
                            this.ckList[i].isCheked = true
                            // this.isShowCk1 = true
                        }
                        else if(this.count ===2){
                            this.ckData2 = this.ckList[i].data
                            this.ckList[i].isCheked = true
                            // this.isShowCk2 = true
                        }
                    }
                    if(this.count>2){
                        alert('2개 이상 선택 불가합니다.')
                        for(let i=0 ; this.ckList.length ; i++){
                            this.ckLimit(type)
                            this.ckData1=data
                            this.ckData2=''
                            this.isShowCk2 = false
                        }
                        return
                                }
                }

                if(this.count===0){
                    this.isShowCk1 = false
                    this.isShowCk2 = false
                }
                else if(this.count===1){
                    this.isShowCk1 = true
                    this.isShowCk2 = false
                }
                                else if(this.count===2){
                    this.isShowCk1 = true
                    this.isShowCk2 = true
                }
            }
        },
        ckLimit(ck){
            switch(ck){
                case 0 :
                    this.ckList[0].isCheked=true
                    this.ckList[1].isCheked=false
                    this.ckList[2].isCheked=false
                    this.ckList[3].isCheked=false
                    break
                case 1 :
                    this.ckList[0].isCheked=false
                    this.ckList[1].isCheked=true
                    this.ckList[2].isCheked=false
                    this.ckList[3].isCheked=false
                    break
                                case 2 :
                    this.ckList[0].isCheked=false
                    this.ckList[1].isCheked=false
                    this.ckList[2].isCheked=true
                    this.ckList[3].isCheked=false
                    break
                                case 3 :
                    this.ckList[0].isCheked=false
                    this.ckList[1].isCheked=false
                    this.ckList[2].isCheked=false
                    this.ckList[3].isCheked=true
                    break
            }  
        }
    }
}
</script>