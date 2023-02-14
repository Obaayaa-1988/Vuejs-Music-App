<template>
  <div id="app">
    <header>
      <h1> MY MUSIC</h1> 
    </header>
    <main>
      <section class="player">
        <h2 class="song-title"> {{ current.title }} -<span>{{ current.artist }}</span></h2>
        <!-- {{  songs[0].src }} -->
        <div class="control"> 
          <button class="prev" @click="prev">Prev</button>
          <button class="play" v-if="!isPlaying">Play</button>
          <button class="pause" v-else @click="pause">Pause</button>
          <button class="next" @click="next">Next</button>

        </div>

      </section >

      <section class="playlist">
       <h3> The Playlist</h3> 
       <button v-for="song in songs" :key="song.src" @click="play(song)" :class="(song.src === 
        current.src) ? 'song playing' :'song'">
        {{ song.title  }} - {{ song.artist }}
      
      </button>


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

  methods: {
    play(song){
      if(typeof song.src != "undefined"){
        this.current = song;

        this.player.src= this.current.src;
      }

      this.player.play();
      this.isPlaying = true;
      this.isPlaying = false;


    },

    pause(){
      this.player.pause();
      this.isPlaying = false;

    },

    next(){
      this.index++;
      if(this.index > this.songs.length -1){
        this.index = 0;
      }
      this.current = this.songs[this.index];
      this.play(this.current);
    },

    

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
