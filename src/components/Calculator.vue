<template>
     <h1 class="mb-8 text-3xl font-bold uppercase">Calculator</h1>
    <div class="p-3" style="max-width: 4000px; margin: 50px auto; background: #234">

        <div class="w-full rounded m-1 p-3 text-right lead font-weight-bold text-white bg-vue-dark">
        <b>Expression</b> = {{ totalString }}
        </div>
         
        <div class="w-full rounded m-1 p-3 text-right lead font-weight-bold text-white bg-vue-dark">
        <b>Result</b> = {{ Result }}
        </div>


        <div class="row no-gutters">
            <div class="col-3" v-for="n in calculatorElements" :key="n">
                <div class="lead text-white text-center m-1 py-3 bg-vue-dark rounded hover-class"
                :class="{'bg-vue-green': ['C','*','/','-','+','%','='].includes(n)}"
                @click="action(n)">
                    {{ n }}
                </div>
            </div>
        </div>
        

    </div>
</template>

<script>
export default {
    name:'Calculator',
    props:{
        msg:String
    },

    data() {
        return{
            flag:false,
            totalString:'Empty',
            Result:0,
            calculatorElements: ['C','*','/','-',7,8,9,'+',4,5,6,'%',1,2,3,'=',0,'.'],
        }
    },


    methods:{
        action(n){
            if(this.totalString === 'Empty' || this.totalString==='Wrong expression' || this.totalString==='0'){
                this.totalString = '';
            }
            if(!isNaN(n) || n== '.'){
                this.totalString+=n+'';
                this.flag = false;
            }

            if(n === 'C'){
                this.totalString='Empty';
                this.Result=0;
                this.flag=false;
            }

            if(['/','*','-','+','%'].includes(n)){
                this.totalString+=n+'';
                if(this.flag){
                    console.log("super");
                    this.totalString = 'Wrong expression'
                }
                this.flag = true;
            }

            if(n==='1' || n==='2' || n==='3'||n==='4'||n==='5'||n==='6'||n==='7'||n==='8'||n==='9'){
                this.Result = eval(this.totalString);
            }

            if(n === '='){
                if(!this.flag) {
                    this.Result = eval(this.totalString);
                    this.totalString = this.Result;
                }else{
                    this.totalString = 'Empty';
                    this.Result = 0;
                }
            }
        }
    }
}
</script>

<style scoped>
h1{
    text-align: center;
}
  .bg-vue-dark {
    background: #31475e;
  }
  .hover-class:hover {
    cursor: pointer;
    background: #3D5875;
  }
  .bg-vue-green {
    background: #3fb984;
  }
</style>