<template>
  <div id="top" class="bg-cover bg-no-repeat bg-center flex items-center justify-center h-screen">
<div class="w-full max-w-xs">
  <div v-if="alertOpen">
  <div class="pb-4" v-if="errors.length">
  <div class="flex bg-red-100 border border-red-400 text-red-700 px-4 py-3 rounded relative" role="alert">
  <div class="py-1"><svg class="fill-current h-5 w-5 text-read-500 mr-4" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"><path d="M2.93 17.07A10 10 0 1 1 17.07 2.93 10 10 0 0 1 2.93 17.07zm12.73-1.41A8 8 0 1 0 4.34 4.34a8 8 0 0 0 11.32 11.32zM9 11V9h2v6H9v-4zm0-6h2v2H9V5z"/></svg></div>
  <ul>
      <li v-for="error in errors" :key="error">{{ error }}</li>
    </ul>
  <span v-on:click="closeAlert()" class="absolute top-0 bottom-0 right-0 px-4 py-3">
    <svg class="fill-current h-6 w-6 text-red-500" role="button" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"><title>Close</title><path d="M14.348 14.849a1.2 1.2 0 0 1-1.697 0L10 11.819l-2.651 3.029a1.2 1.2 0 1 1-1.697-1.697l2.758-3.15-2.759-3.152a1.2 1.2 0 1 1 1.697-1.697L10 8.183l2.651-3.031a1.2 1.2 0 1 1 1.697 1.697l-2.758 3.152 2.758 3.15a1.2 1.2 0 0 1 0 1.698z"/></svg>
  </span>
</div>
</div>
  </div>

  <form class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4">
    <div class="mb-4">
      <label class="block text-gray-700 text-sm font-bold mb-2" for="username">
        Finding the first non unique character in a string
      </label>
      <input v-model="data" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="character" type="text" placeholder="Enter word!">
    </div>
    <div class="flex w-full justify-center">
     
        <button v-if="buttonShow" @click.prevent="submit" class="bg-purple-500 hover:bg-purple-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline" type="submit">
          Search
        </button>
        <!-- <button v-if="buttonShow" @click.prevent="Clean" class="bg-red-500 hover:bg-red-700 text-white font-bold py-2 px-5 pl-5 rounded focus:outline-none focus:shadow-outline" type="submit">
          Clear
        </button> -->
        <div v-if="imgShow">
          <iframe  id="giff" src="https://giphy.com/embed/Bve8CDLZCFuZa" width="100" height="100" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="https://giphy.com/stickers/pikachu-Bve8CDLZCFuZa"></a></p>
          <p>Processing...</p>
        </div>
     
    </div>
   <h1 class="flex pt-2">Output: <p class="pl-2" id = "display">{{ output }}</p></h1>

  </form>
  

</div>
  </div>
</template>

<script>
export default {
  name: 'UniqueCharacter',
  data() {
    return {
      errors: [],
      data: '',
      output: '',
      alertOpen: true,
      imgShow: false,
      buttonShow: true,
    }
  },
  methods:{
      Clean(){
    document.getElementById('display').innerHTML='';
    },
    closeAlert: function(){
      this.alertOpen = false;
    },
    submit(e) {
    for (let i = 0; i < this.data.length; i++) {
    let check = this.data[i];
    if (this.data.indexOf(check) == i && this.data.indexOf(check, i + 1) == -1) {
      setTimeout(() => this.output = check, 5000);
      setTimeout(() => this.buttonShow = true, 5000);
      setTimeout(() => this.imgShow = false, 5000);
      this.imgShow = true;
      this.buttonShow = false
    }
  }
  this.errors = [];
  if (this.data) {
        return true;
      }

      this.errors = [];

      if (!this.data) {
        this.errors.push('Word required!');
        this.alertOpen = true
      }
     
      e.preventDefault();
    },
  
  }
 
}


</script>
<style>
#top {
    background: url(/src/assets/bg.jpg);
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
}
</style>
<!-- Add "scoped" attribute to limit CSS to this component only -->

