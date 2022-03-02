<template>
    <div>
        
    </div>
</template>

<script>
export default {
    data() {
        return {
            ckList:[],
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
        }    
    },
}
</script>
