<template>
  <div id="app">
    <Footer>
      <template v-slot:column-A>
        <Sources :title='sources.title' :sources_list="sources.list" />
      </template>
      <template v-slot:column-B>
        <Update :title="update.title" :date="update.date" :alert="update.alert" />
        <Resume :title="'Teste desenvolvido por:'" />
      </template>
    </Footer>
  </div>
</template>

<script>
import Footer from '@/components/Footer.vue';
import Sources from '@/components/Sources.vue';
import Update from '@/components/Update.vue';
import Resume from '@/components/Resume.vue';

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
        title: 'Atualizado em:',
        date: new Date().getTime(),
        alert: 'Os dados são atualizados de hora em hora.'
      }
    }
  },
  components: {
    Footer,
    Sources,
    Update,
    Resume
  }
}
</script>

<style lang="scss">
  // Reset default browser styles
  @import "@/scss/lib/_reset.scss";
</style>
