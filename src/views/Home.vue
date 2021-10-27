<template>
  <div class="w-full h-full bg-gray-100 flex flex-col">
    <!-- Header section -->
    <div class="header h-16 bg-white shadow-md flex">
      <div class="flex h-full w-20 justify-center items-center bg-blue-400 text-white font-bold text-2xl z-">
        lF3D
      </div>
    </div>
    <!-- End header section -->
    <!-- body section -->
    <div class="body w-full h-full p-44 flex flex-col justify-center items-center">
      <div class="flex flex-col w-2/6 ">
        <p class="text-gray-400 text-xl mb-4">Connect to the database to start</p>
        <div class="loginForm w-full p-10 bg-white rounded-xl shadow-lg">
          <p class="text-2xl text-blue-400">Server Information</p>
          <div class="grid grid-cols-1 gap-5 my-10">
            <l-form  :model="db.host" placeholder="Ex: https://www.luk3d.com">
            <template v-slot:label> Host </template>
          </l-form>
          
          <l-form class="mt-5"  :model="db.user" placeholder="Ex: root">
            <template v-slot:label> Username </template>
          </l-form>
          <l-form class="mt-5"  :model="db.pwd" placeholder="">
            <template v-slot:label> Password </template>
          </l-form>

          <l-button @click="testConnection(db)"></l-button>

          <p class="text-md m-0 p-0 text-gray-400">Select a Database</p>
          <l-form position="top" :options="options" type="select" class="-mt-4"  :model="db.db" placeholder="Ex: LUK3D">
            <template  v-slot:label> Database </template>
          </l-form>
          
          </div>
        </div>
      </div>
    </div>
    <!-- end body section  -->
  </div>
</template>

<script>
// @ is an alias to /src
import lForm from '@/components/l-form.vue';
import lbutton from '@/components/l-button.vue';
export default {
  name: 'Home',
  components: {
    'l-form':lForm,
    'l-button':lbutton,
  },

  methods:{
    testConnection(val){
      console.log(val)
    }
  },

  data(){
    return{
      db:{},
      options:[
        {label:"Realhope"},
        {label:"Eventus"},
        {label:"LLCars"}
      ]
    }
  },
}
</script>
