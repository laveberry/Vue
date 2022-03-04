<template>
    <div>
        <check-box v-model="ckList[0].isCheked" :disabled="disCk" @change="onchange(0,'ck1')"><span>체크박스1</span></check-box>
        <check-box v-model="ckList[0].isCheked" :disabled="disCk" @change="onchange(1,'ck2')"><span>체크박스2</span></check-box>
        <check-box v-model="ckList[0].isCheked" :disabled="disCk" @change="onchange(2,'ck3')"><span>체크박스3</span></check-box>
        <check-box v-model="ckList[0].isCheked" :disabled="disCk" @change="onchange(3,'ck4')"><span>체크박스4</span></check-box>
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
            count:0 //초기카운트
        }
    },
    methods: {
        onchange(type, data){
            this.count=0
            for(let i=0 ; this.ckList.length ; i++){
                if(this.ckList[i].isCheked){
                    this.count++
                if(this.count===1){
                    this.ckData1 = this.ckList[i].data
                    this.isShowCk1 = true
                }
                else if(this.count ===2){
                    this.ckData2 = this.ckList[i].data
                    this.isShowCk2 = true
                     
                }
                    }
                    if(this.count>2){
            for(let i=0 ; this.ckList.length ; i++){
                this.ckLimit(type)
                this.ckData1=data
                this.ckData2=''
                this.isShowCk2 = false
            }
            return
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

            }
        }    
    },
}
</script>
