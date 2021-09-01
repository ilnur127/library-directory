<template>
    <div style="display:flex;">
        <div style="margin-left: 60px;">
            <div
                class="card-block_left"
                v-for="g of recordData.general"
                :key="g"
            >
                <div class="dot"></div>
                <div style="width:100%">
                    <div
                        v-for="data of g.data"
                        :key="data"
                    >
                        {{data}}
                    </div>
                </div>
            </div>
            <div
                class="card-block_left"
            >
                <div class="dot"></div>
                <div style="width:100%;">
                    <div
                        v-for="data in recordData.timeWork.data"
                        :key="data"
                    >
                        <strong>{{data.day}}</strong> {{data.time}}
                    </div>
                </div>
            </div>
        </div>
        <div style="margin-left: 170px;">
            <div
                class="card-block_left"
            >
                {{recordData.info.data}}
            </div>
        </div>
    </div>
    <div style="width: 100%;display: flex;margin-left: 60px;margin-top: 30px;color: #C7884A;">
        <div
            v-for="(data, i) of recordData.tags.data"
            :key="data"
            style="margin-right:10px;"
        >
            {{getTag(data.name,i,recordData.tags.data.length)}}
        </div>
    </div>
    <div style="margin: 15px 0px;">
        <div style="display: flex;justify-content: space-evenly;">
            <img src="../assets/Rectangle15.png" alt="">
            <img src="../assets/Rectangle15.png" alt="">
            <img src="../assets/Rectangle15.png" alt="">
            <img src="../assets/Rectangle15.png" alt="">
        </div>
        <div>
            <img src="../assets/Ellipse2.png" style="margin:0px 10px" alt="">
            <img src="../assets/Ellipse1.png" style="margin:0px 10px" alt="">
            <img src="../assets/Ellipse2.png" style="margin:0px 10px" alt="">
        </div>
    </div>
</template>

<script>
export default {
  name: 'mainBlock',
  data: () => ({}),
  props: ['recordData'],
  methods: {
    getTag (tag, i, length) {
      let tagStr = `#${tag}`
      if (i !== length - 1) {
        tagStr += ', '
      }
      return tagStr
    },
    getImgUrl (image) {
      return `../assets/${image}.svg`
    }
  }
}
</script>
