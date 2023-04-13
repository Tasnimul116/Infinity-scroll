<template>
  <div>
    <header>
      <h1>My Anime Feed</h1>
    </header>

    <main>
      <div>
        <BlogPost v-for="(anime, i) in anime_list" :key="i" :anime="anime" />
      </div>
      
    </main>
  </div>
</template>

<script>
import BlogPost from './components/BlogPost.vue';

export default {
  name: 'App',

  components: {
    BlogPost
  },

  data() {
    return {
      anime_list: []
    };
  },

  mounted() {
    this.anime_list = this.getAnime();
    window.addEventListener('scroll', this.handleScroll);
  },

  methods: {
    getAnime() {
      const anime_title = [
        'Attack on Titan',
        'Death Note',
        'Fullmetal Alchemist',
        'One Piece',
        'Naruto',
        'Spirited Away',
        'Your Lie in April',
        'Demon Slayer: Kimetsu no Yaiba',
        'My Hero Academia',
        'Cowboy Bebop',
        'Neon Genesis Evangelion',
        'Dragon Ball Z'
      ];

      const anime = [];
      for (let i = 0; i < 10; i++) {
        anime.push({
          title: anime_title[Math.floor(Math.random() * anime_title.length)],
          description:
            'Lorem ipsum dolor sit amet consectetur adipisicing elit. Atque cum reprehenderit aliquid ipsum pariatur possimus, dolor quae architecto delectus provident repudiandae velit, sunt, laboriosam sequi. Vel minus eius ipsum maiores?'
        });
      }
      return anime;
    },
    handleScroll() {
      if (window.scrollY + window.innerHeight >= document.body.scrollHeight - 50) {
        const new_anime = this.getAnime();
        this.anime_list = [...this.anime_list, ...new_anime];
      }
    }
  }
};
</script>


<style>
  * {
    margin: 0;
    box-sizing: border-box;
  }

  body {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    background: rgb(131, 58, 180);
    background: linear-gradient(
      352deg,
      rgba(131, 58, 180, 1) 0%,
      rgba(253, 29, 29, 1) 54%,
      rgba(252, 176, 69, 1) 100%
    );
    color: white;
    min-height: 100vh;
    padding-top: 3rem;
  }

  header h1 {
    margin-bottom: 2rem;
    text-align: center;
  }

  main {
    padding: 0.2rem;
    max-width: 640px;
    margin: 0 auto;
    display: flex;
    flex-direction: column;

  }
</style>
