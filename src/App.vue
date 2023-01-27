<template>
  <div id="app">
    <header>
      <h1> MY MUSIC</h1> 
    </header>
    <main>
      <section class="music-player">
        <h2 class="song-title"> {{ current.title }} </h2>
        {{  songs[0].src }}

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
        // title: "SONG TITLE"              /**data for current song */
      },
      index: 0,
      isPlaying: false,
      songs: [
        {
          title: 'Grateful',
          artist: 'Neffex',
          src: require('./assets/neffex-grateful.mp3')
        },
        {
          title: 'Invincible',
          artist: 'Def Kev',
          src: require('./assets/deaf-kev-invincible.mp3')
        },
      ],
      player: new Audio(),
    }
  },

  created(){
    this.current = this.songs[this.index];
    this.player.src = this.current.src;
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
