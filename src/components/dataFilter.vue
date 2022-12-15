<template>
  <div class="holder">
    <label for="DiscountType">Discount: </label>
    <select name="" id="DiscountType" v-model="this.selectedDiscount" @change="this.choseDiscount($event)">
        <option value="WinCasaPartners">WinCasa Partners</option>
        <option value="WinCasaDiscount">WinCasa Discount</option>
        <option value="Jarowa">Jarowa</option>
        <!-- <option v-for="(value,index) in this.dataIn" :key="index"  :value="value.">{{value.Name}}</option> -->
    </select>
  </div>
</template>

<script>
export default {
    data:function()
    {
        return {
            selectedDiscount:""
        }
    },
    mounted:function(){
    },
    methods:{
        choseDiscount:function(){
            // alert(event)
            //SD % FR
            switch (this.selectedDiscount){
                case "WinCasaPartners":
                    this.$emit("SortFunction",this.generalSort,[3,2,1],this.selectedDiscount)
                break;
                case "WinCasaDiscount":
                    this.$emit("SortFunction",this.generalSort,[2,3,1],this.selectedDiscount)
                break;
                case "Jarowa" :
                    this.$emit("SortFunction",this.generalSort,[3,1,2],this.selectedDiscount)
                break;
            }
        },
        sortFlatRate:function(Arr,PropName){
            Arr.sort(function({[PropName]:a},{[PropName]:b}){
                if (isNaN(a) || isNaN(b))
                    return 0
                let ValA = parseInt(a);
                let ValB = parseInt(b);
                console.log(`${ValB} - ${ValA} = ${ValB - ValA}`)
                return ValB - ValA;
            })
        },
        sortPercent:function(Arr,PropName){
            Arr.sort(function({[PropName]:a},{[PropName]:b}){
                if (!a.includes("%") || !b.includes("%"))
                    return 0;
                let ValA = parseInt(a);
                let ValB = parseInt(b);
                return ValB - ValA;
            })
        },
        generalSort:function(Arr,Values,Field){
            Arr.sort(function({[Field]:a},{[Field]:b}){
                let ValA = 0
                let ValB = 0
                if (a == "SD")
                    ValA = Values[0]
                else if ( a.includes("%"))
                    ValA = Values[1]
                else ValA = Values[2]

                if (b == "SD")
                    ValB = Values[0]
                else if ( b.includes("%"))
                    ValB = Values[1]
                else ValB = Values[2]
                return ValB - ValA;
            })
            this.sortFlatRate(Arr,Field);
            this.sortPercent(Arr,Field);
        }
    }
}
</script>

<style scoped>
    .holder{
        display: flex;
        background-color: brown;
        justify-content: center;
        align-items: center;
        margin: 5% 5%;
        padding: 5% 5%;
        font-size: 1.5rem;
    }
    option{
        /* color: green; */
        font-size: 1.5rem;
    }
    select{
        background-color: #232323;
        margin: 0% 2%;
        font-size: 1.5rem;
    }
</style>