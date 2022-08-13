<template>
  <div>
    <section>
      
      <article v-for="song in songs" :key="song[`song_id`]">
        <p>{{ song[`title`] }}</p>
        <p>{{ song[`artist`] }}</p>
        <img
          :src="song[`img_url`]"
          alt=""
          @click="ChosenMusic"
          :song_id="song[`song_id`]"
        />
      </article>
    </section>
    <div v-if="song_being_listened === false">
      <h2>Pick a song</h2>
    </div>

    <div class="chosen_music">

    </div>
  </div>
</template>

<script>
export default {
  
  methods: {
    /* Users song chose details  */
    ChosenMusic(details) {
      this.song_being_listened = true;
      /* Song ID */
      let song_id = details[`target`].getAttribute(`song_id`);
      for(let i = 0; i < this.songs.length; i++) {
        if(this.songs[i][`song_id`] === song_id) {
            let chosen_music = document.querySelector(`.chosen_music`);
            chosen_music[`innerHTML`] = `
            <h2>Listening to</h2>
            <h3>${this.songs[i][`title`]}</h3>
            <img src="${this.songs[i][`img_url`]}">
            `
        }
      }
    },
  },

  data() {
    return {
      /* Telling user to pick a song */
      song_being_listened: false,
      /* Details of array : Artist name, song name, and song ID */ 
      songs: [
        {
          title: `Proud of myself`,
          artist: `YoungBoy `,
          song_id: `10`,
          img_url:  ` https://i.scdn.co/image/ab67616d0000b2736fff08fad874ee9936489d09   `,
        },
        {
          title: `Fire and desire`,
          artist: `Drake`,
          song_id: `20`,
          img_url: `https://i1.sndcdn.com/artworks-Z19d1jdImMbt-0-t500x500.jpg`,
        },
        {
          title: `Keeper`,
          artist: `Toosii`,
          song_id: `30`,
          img_url: ` https://i1.sndcdn.com/artworks-yttGkz8AYKPb-0-t500x500.jpg `,
        },
      ],
    };
  },
};
</script>

<style scoped>
section {
  grid-template-columns: 1fr 1fr 1fr;
  display: grid
  
}
img {
  width: 200px;
  height: 200px;
}
</style>
