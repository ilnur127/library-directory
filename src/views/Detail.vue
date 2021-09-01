<template>
  <Loader v-if="loading" />
  <div
    v-else
  >
    <div
      class="card-title"
      :style="getStyle"
    >
      {{record.name}}
    </div>
    <div style="display:flex;box-shadow: white 0px 33px 73px -5px inset;flex-direction: column;padding-top: 50px;">
      <mainBlock
        :recordData="record"
      />
      <buttons
        :data="leftMenu"
        :photo="record.photo"
      />
    </div>
  </div>
</template>

<script>
import Loader from '../components/Loader.vue'
import mainBlock from '../components/mainBlock.vue'
import buttons from '../components/buttons.vue'
export default {
  name: 'Detail',
  data: () => ({
    loading: true,
    record: null,
    leftMenu: null
  }),
  async mounted () {
    const categories = await require('../data-52-structure-3.json')
    for (const o in categories) {
      if (categories[o]._id === this.$route.params.id) {
        const contacts = []
        const timeWork = [
          {
            day: 'Пн:',
            time: categories[o].data.general.workingSchedule['0'] ? `${categories[o].data.general.workingSchedule['0'].from} - ${categories[o].data.general.workingSchedule['0'].to}` : 'Выходной'
          },
          {
            day: 'Вт:',
            time: categories[o].data.general.workingSchedule['1'] ? `${categories[o].data.general.workingSchedule['1'].from} - ${categories[o].data.general.workingSchedule['1'].to}` : 'Выходной'
          },
          {
            day: 'Ср:',
            time: categories[o].data.general.workingSchedule['2'] ? `${categories[o].data.general.workingSchedule['2'].from} - ${categories[o].data.general.workingSchedule['2'].to}` : 'Выходной'
          },
          {
            day: 'Чт:',
            time: categories[o].data.general.workingSchedule['3'] ? `${categories[o].data.general.workingSchedule['3'].from} - ${categories[o].data.general.workingSchedule['3'].to}` : 'Выходной'

          },
          {
            day: 'Пт:',
            time: categories[o].data.general.workingSchedule['4'] ? `${categories[o].data.general.workingSchedule['4'].from} - ${categories[o].data.general.workingSchedule['4'].to}` : 'Выходной'
          },
          {
            day: 'Сб:',
            time: categories[o].data.general.workingSchedule['5'] ? `${categories[o].data.general.workingSchedule['5'].from} - ${categories[o].data.general.workingSchedule['5'].to}` : 'Выходной'
          },
          {
            day: 'Вс:',
            time: categories[o].data.general.workingSchedule['6'] ? `${categories[o].data.general.workingSchedule['6'].from} - ${categories[o].data.general.workingSchedule['6'].to}` : 'Выходной'
          }
        ]
        for (const c of categories[o].data.general.contacts.phones) {
          contacts.push(c.value)
        }
        contacts.push(categories[o].data.general.contacts.email)

        this.record = {
          name: categories[o].nativeName,
          info: {
            icon: 'mainInfo',
            data: categories[o].data.general.description.replace(/<p>/g, '').replace(/<\/p>/g, '')
          },
          general: {
            site: {
              icon: 'webSite',
              data: [
                categories[o].data.general.contacts.website
              ]
            },
            contacts: {
              icon: 'phone',
              data: contacts
            },
            place: {
              icon: 'place',
              data: [
                categories[o].data.general.organization.address.fullAddress
              ]
            }
          },
          timeWork: {
            icon: 'timeWork',
            data: timeWork
          },
          tags: {
            icon: 'place',
            data: categories[o].data.general.tags
          },
          photo: {
            url: categories[o].data.general.image.url,
            title: categories[o].data.general.image.title
          }
        }
        this.leftMenu = {
          site: {
            url: this.record.general.site.data[0],
            text: 'Перейти на сайт'
          },
          write: {
            url: contacts[contacts.length - 1],
            text: 'Написать'
          },
          call: {
            url: contacts[0],
            text: 'Позвонить'
          }
        }
      }
    }

    console.log(categories)
    console.log(this.record)
    this.loading = false
  },
  computed: {
    getStyle () {
      console.log('1')
      return `background-image: url('${this.record.photo.url}');box-shadow: white 0px -92px 73px -5px inset;`
    }
  },
  components: {
    Loader,
    mainBlock,
    buttons
  }
}
</script>

<style>
  .card-title {
    display: flex;
    align-items: flex-end;
    justify-content: flex-end;
    height: 311px;
    font-family: Roboto;
    font-style: normal;
    font-weight: bold;
    font-size: 66px;
    padding-bottom: 50px;
    opacity: 0.8;
  }
  .card-title--img {
    width: 300px;
    border-radius: 50%;
  }
  .card-block_left {
    text-align: left;
    display:flex;
    align-items: center;
  }
  .dot {
    width: 10px !important;
    height: 10px !important;
    background: #2f7b59;
    border-radius: 5px;
    margin: 10px;
  }
</style>
