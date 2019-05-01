<script>
import {default as tabitem} from './tab_btn.vue'
export default {
    name: 'Otzartabs', // vue component name
    data() {
        return {
           is_ltr:true,
           tabs:[]
        };
    },
    props:['ltr'],
    components:{tabitem} ,
    methods:{
        setDirection(rtl=true){
                this.is_ltr=!rtl;
        },
        addTab(html="",id=(Math.random() * 100000000)){
                this.tabs.push({
                    html,
                    id
                });
        },
        removeTab(id){
            this.tabs.forEach((e,i) =>{
                if(e.id==id) this.tabs.splice(i, 1);
            })  
        }
    },
    created(){
        this.is_ltr=this.ltr;
    }
}
</script>

<template>
    <div class="tabs_header" :class="{tabs_header_ltr: is_ltr}">
        
        <div>
            <slot></slot>
            <tabitem v-for="tab in tabs" :key="tab.id">{{tab.html}}</tabitem>
        </div>
        
         <div class="tabs_hamburger_btn" :class="{tabs_hamburger_btn_ltr: is_ltr}">
            <div></div>
            <div></div>
            <div></div>
        </div> 

    </div>  
</template>

<style scoped>
    .tabs_header{
        stroke:#009687;
        fill:#00A6A6;
        padding-top:3px;
        background-color:#05C6BC;
        height: 55px;
        overflow: hidden;
        text-align: right;
        font-family:Heebo;
        direction: rtl;
    }
    .tabs_header_ltr{
        direction: ltr;
        text-align: left;
    }
    .tabs_hamburger_btn{
        display: none
    }
    @media (max-width: 48em) {
        .tabs_hamburger_btn {
            display: block;
            float: left;
            padding: 0px;
            margin: 5px;
            cursor: pointer;
        }
        .tabs_hamburger_btn_ltr {
            display: block;
            float: right;
            padding: 0px;
            margin: 5px;
            cursor: pointer;
        }
        .tabs_hamburger_btn div{
            width: 35px;
            height: 5px;
            background-color: white;
            margin: 6px 6px;
        }
        
    }
    
</style>
