<template>

    <div class="tab_item" :class="{active: is_active,tab_item_ltr: $parent.is_ltr}" >
        <div class="tab_content" @click.prevent="setActive($event)"><slot></slot></div>
        <svg xmlns="http://www.w3.org/2000/svg" class="tab_svg" viewBox="0 0 114.72 37.7"><g id="Layer_2" data-name="Layer 2"><g id="Layer_1-2" data-name="Layer 1"><path id="Path_22" data-name="Path 22" d="M.46,36.5,12.14,9.05C13.8,3.5,16.39.5,20.17.5H94.54c3.79,0,6.38,3,8,8.55L114.26,36.5" style="stroke-linejoin:bevel"/></g></g></svg>    
    </div>

</template>

<script >
    

    export default {
        name: 'tabitem',
        props:{
            is_active:{
                default:false
            }
        },
        methods:{
            setActive($event){
                //get all tab_item elements
                let tab_items = this.$el.parentElement.getElementsByClassName("tab_item");
                //loop through them and remove the active class
                for(var i = 0; i < tab_items.length; i++)
                    tab_items.item(i).className=tab_items.item(i).className.replace("active","");

                //locate the tab_item element
                let selectedElement=this.findUpName($event.target,"tab_item");
                //add active class to it
                let addClassString=selectedElement.className.concat(" active").replace(/\s+/g, ' ')
                //apply the active class
                selectedElement.className=addClassString;            
                //trigger the event
                selectedElement.parentNode.parentNode.dispatchEvent(new CustomEvent('tab_click',{ detail: selectedElement}));
            },

            findUpName(el, name) {
                while (el.parentNode) {
                    el = el.parentNode;                  
                    if (el.className.includes(name))
                        return el;
                }
                return null;
            }
        }
    }
</script>

<style scoped>
.tab_item:hover{
        text-shadow: 4px 4px 9px rgba(0,0,0,0.6);

    }
    .tab_item {
        cursor: pointer;
        min-width:200px;
        max-width:400px;
        color: white;
        stroke:#009687;
        fill:#00A6A6;
        display:inline-block;
        position:relative;
        text-align:center;
        height:100%;
        line-height:55px;
        margin-left:-25px;
        overflow: hidden;
        z-index: 0;
    }
    .tab_item_ltr {
        margin-right:-25px;
    }
    .tab_item:last-child {
        margin-left:0px;
        margin-right:0px;
    }
    .tab_item_ltr:first-child {
        margin-left:0px;
        margin-right:0px;
    }
    .tab_content{
        z-index:1;
        margin: 0 auto;
        position:relative;
        vertical-align:middle;
        width:80%;
        height:100%;
        line-height: 55px
    }
    .tab_svg{
        display:inline-block;
        position:absolute;
        width:100%;
        left:0;
        top:0px
    }
    .active{
        fill:#F5F5F5;
        stroke: #F5F5F5;
        z-index: 2;
        color: black;
    }
     @media (max-width: 48em) {
         .tab_item{
            display: none;
        }
     }
</style>