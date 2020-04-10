<template>
  <div id="app">
    <main>
      <section class="main">
        <HomeTitle :hat='"Casos confirmados de"' :title='"Coronavírus"' :subtitle='"no Brasil"' />
        <div class="content">
          <div class="content__row">
            <Case :number="cases.confirmed" :legend="'CASOS CONFIRMADOS'" :color="'yellow'" />
          </div>
          <div class="content__row">
            <Case :number="cases.deaths" :legend="'MORTES CONFIRMADAS'" :color="'red'" />
            <Case :number="cases.recovered" :legend="'CASOS RECUPERADOS'" :color="'blue'" />
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
        date: null,
        alert: 'Os dados são atualizados de hora em hora.'
      },
      cases: {
        confirmed: null,
        deaths: null,
        recovered: null,
      }
    }
  },
  created: function(){
    var app = this;

    app.get_cases().then( async( result ) => {

      if( result.locations ){
        app.set_update_date( result.locations[0].last_updated );
      };

      if( result.latest ){
        app.set_cases( String( result.latest.confirmed ) , String( result.latest.deaths ) , String( result.latest.recovered ) );
      }
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
    set_update_date( last_update ){
      if( last_update ){
        this.update.date = new Date( last_update ).getTime();
      }else{
        this.update.date = 0;
      }
    },
    set_cases( confirmed , deaths , recovered ){
      if( confirmed ){
        this.cases.confirmed = confirmed
      }
      if( deaths ){
        this.cases.deaths = deaths
      }
      if( recovered ){
        this.cases.recovered = recovered
      }
    }
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
