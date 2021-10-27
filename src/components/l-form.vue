<template>
   <div @mouseenter="entered=true" @mouseleave="entered = false" :class="
   (lstyle=='primary')?`${isDirty(model)?'border-gray-200':'border-blue-200'} input flex w-full rounded-lg border-2  p-1 relative`
   :(lstyle=='secondary')?` ${isDirty(model)?'border-blue-200':'border-gray-200'} rounded-0 border-b-2  flex w-full relative p-1 transition-colors`:''
   ">
    <label v-show="lstyle=='primary'" class="text-xl text-gray-400 mx-2 border-r-2 pr-1">
        <slot name="label"></slot>
    </label>
    <label v-show="lstyle=='secondary'" :class="`${isDirty(model)?'bottom-full text-blue-500 mx-0 tex-sm':'bottom-0 text-gray-400 mx-2 text-xl '}     pr-1 absolute  pointer-events-none transition-all duration-500 ease-in-out`">
        <slot name="label"></slot>
    </label>
    <input v-model="model"  @blur="active = true" :placeholder="(lstyle=='primary')?placeholder:''" type="text" class=" w-full outline-none text-gray-500 text-xl">

    <div v-show="entered" v-if="type=='select'" :class="`w-full absolute ${position}-full flex flex-col   bg-white shadow-2xl py-4 rounded-lg`">
        <button @click="entered = false; model = (item.label)" v-for="item in options" :key="item"   class="px-4 py-2 hover:bg-gray-100 w-full text-left flex text-gray-400 focus:bg-blue-100">{{item.label}}</button>
    </div>
    </div>
</template>

<script>
/* eslint no-use-before-define: 0 */
export default {
    props:{
        placeholder:String,
        model:String,
        type:String,
        options:Array,
        'lstyle':{
            type:String,
            default:'secondary'
        },
        position:{
            type:String,
            default:'top'
        }
    },

    computed:{
       
    },
    methods:{
       isDirty(val){
           if(val==null) return false;
           if(val.length>0)return true;
           
           return false;
       }
    },

    data(){
        return{
            active:false,
            entered:false,
          
        
        }
        
    },

}
</script>

<style>

</style>