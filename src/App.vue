<template>
  <div id="app">
    <header>
      <h1> MY MUSIC</h1> 
    </header>
    <main>
      <section class="music-player">
        <h2 class="song-title"> {{ current.title }} </h2>

      </section>

    </main>
    
  </div>
</template>

<script>



export default {
  name: 'App',
  components: {
  },

  data(){
    return{
      current:{
        title: "SONG TITLE"/**data for current song */
      }
    }
  }


}
</script>

<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

header{
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #212121;
  padding: 15px;
  color: #fff;
}
</style>
