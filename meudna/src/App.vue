<template>
  <div id="app">
    <main>
      <section class="main">
        <HomeTitle :hat='"Casos confirmados de"' :title='"Coronavírus"' :subtitle='"no Brasil"' />
        <div class="content">
          <div class="content__row">
            <Case :number="14000" :legend="'CASOS CONFIRMADOS'" :color="'yellow'" />
          </div>
          <div class="content__row">
            <Case :number="700" :legend="'MORTES CONFIRMADAS'" :color="'red'" />
            <Case :number="0" :legend="'CASOS RECUPERADOS'" :color="'blue'" />
          </div>
          <div class="content__row">
            <Update :title="'Atualizado há'" :date="update.date" :alert="update.alert" :compact="true" />
          </div>
        </div>
      </section>
    </main>
    <Footer>
      <template v-slot:column-A>
        <Sources :title='sources.title' :sources_list="sources.list" />
      </template>
      <template v-slot:column-B>
        <Update :title="'Atualizado em:'" :date="update.date" :alert="update.alert" />
        <Resume :title="'Sobre o teste:'" />
      </template>
    </Footer>
  </div>
</template>

<script>
import Footer from '@/components/Footer.vue';
import Sources from '@/components/Sources.vue';
import Update from '@/components/Update.vue';
import Resume from '@/components/Resume.vue';
import HomeTitle from '@/components/HomeTitle.vue';
import Case from '@/components/Case.vue';

export default {
  name: 'App',
  data: function () {
    return {
      sources: {
        title: 'Fontes:',
        list: [
          {
            title: '(JHU CSSE)',
            desc: 'Johns Hopkins University Center for Systems Science and Engineering',
            links: [
              {
                name: 'Website',
                url: 'https://systems.jhu.edu/'
              },
              {
                name: 'Repositório',
                url: 'https://github.com/CSSEGISandData/COVID-19'
              },
            ]
          },
          {
            title: '(CSBS)',
            desc: 'U.S. County data that comes from the Conference of State Bank Supervisors',
            links: [
              {
                name: 'Website',
                url: 'https://www.csbs.org/'
              },
              {
                name: 'Repositório',
                url: 'https://www.csbs.org/information-covid-19-coronavirus'
              },
            ]
          }
        ]
      },
      update: {
        date: 0,
        alert: 'Os dados são atualizados de hora em hora.'
      },
    }
  },
  created: function(){
    var app = this;
    app.get_cases().then( async( result ) => {
      app.update.date = new Date().getTime();
      console.log( app.update.date );
      console.log( result );
    });

  },
  methods: {
      async get_cases(){
        const result = await fetch( 'https://coronavirus-tracker-api.herokuapp.com/v2/locations?country_code=BR' , { method:'GET' } )
        .then(response => response.json())
        .catch(function(error) {
            console.error( `get_cases(): \n ${error}` )
            return error
        })
        .then(function(response) {
          return response
        })

        return await result
    },
  },
  components: {
    Footer,
    Sources,
    Update,
    Resume,
    HomeTitle,
    Case
  }
}
</script>

<style lang="scss">
  // Reset default browser styles
  @import "@/scss/lib/_reset.scss";
  @import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;500&display=swap');

  body{
    background-color: $bluewood;
    font-family: 'Roboto' , helvetica, arial, sans-serif;
    color: $white;
  }

  a{
    color: $cream;
    text-decoration: none;
  }

  .main{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    background-image:
      linear-gradient(rgba(44, 62, 80, 0.8), rgba(44, 62, 80, 0.8)),
      url( "./assets/background.jpeg" );
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    padding: 3rem 0;


    .case{
      margin: 0 1rem 2rem;
    }
  }

  .content{
    @extend %limit;
    text-align: center;

  }
</style>
