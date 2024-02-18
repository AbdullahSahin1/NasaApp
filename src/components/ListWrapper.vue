<template>
    <div class="inputWrapper">  
        <input v-model="q" autofocus placeholder="Uzayda bir şeyler arayın"></div>
        <div class="listwrapper">
            <div v-for="item in data">
                <ListItem :item="item"/>
            </div>
        </div>
        <div class="nodata" v-if="data.length===0 && loading==false">Uzayda Boşluk var</div>
        <div class="nodata" v-if="loading==true">
            <Loading></Loading>
        </div>

</template>

<script>
import Loading from './Loading.vue'
import ListItem from './ListItem.vue'
export default {
  methods: {
    FetchData(q) {
        this.loading= true
        fetch('https://images-api.nasa.gov/search?q='+q).then((res)=>{
            res.json().then((d)=>{
                console.log(d)
                this.loading= false;    
                this.data= d.collection.items
            })
        })
    },
  },
    created() {

    },
    data () {
    return {
        loading: false,
        data:[],
        q: "",
    }
  },
  components: {
        Loading,
        ListItem,
    },
  watch:{
    q(newVal,oldVal) {
        if(newVal.length > 2){
            this.FetchData(newVal)
        }
        else{
            this.FetchData(oldVal)
            this.data = []
        }
    }
  },
    name: 'ListWrapper',
}
</script>

<style>
    .listwrapper{
    display: grid;
    grid-template-columns: repeat(4,1fr);
    gap: 20px;
}
.nodata{
    text-align: center;
    width: 100%;
    color: #fff;
    font-size: 32px;
}
    .inputWrapper{
        width: 100%;
        display: flex;
        margin-bottom: 20px;
    }
    .inputWrapper > input{
        height: 40px;
        display: flex;
        padding: 8px 16px;
        box-sizing: border-box;
        border: none;
        outline: none;
        border-radius: 16px;
        text-transform: uppercase;
        width: 100% ;
        background-color: aliceblue;
    }
</style>