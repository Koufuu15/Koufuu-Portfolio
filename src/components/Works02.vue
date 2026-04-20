<template>
  <div class="works-section">

    <h1>Works</h1>

    <div class="slider">

      <div
        class="slides"
        :style="{ transform:`translateX(${offset}px)` }"
      >

        <div
          class="card"
          v-for="(work,i) in works"
          :key="i"
        >
          <h3>
            <a :href="work.link" target="_blank" rel="noopener noreferrer">{{work.title}}</a>
          </h3>
          <p>{{work.date}}</p>
          <span class="label" :style="{ backgroundColor: labels[work.category] }">
            {{work.category}}
          </span>
          <p style="margin-top:10px;" class="description">
            {{work.description}}
          </p>
        </div>

      </div>

    </div>

    <!-- dots -->
    <div class="dots">
      <span
        v-for="(w,i) in works"
        :key="i"
        :class="{active: i===current % works.length}"
        @click="current=i"
      ></span>
    </div>

  </div>
</template>

<script>
import {ref,onMounted,computed} from "vue"

export default {

  setup(){

    const works = [
      {title:"Zenn",date:"Since 2025",category:"Blog",link:"https://zenn.dev/koufu",description:"技術ブログ。主にCTFやセキュリティに関する内容を投稿しています。"},
      {title:"Qiita",date:"Since 2025",category:"Blog",link:"https://qiita.com/nade_3356",description:"技術ブログ。学校のオーガニゼーションと結びついています。"},
      {title:"CognitiveHack Japan",date:"2026.3",category:"CTF",link:"https://cognitivehack-jp.cognitivectf.com/",description:"中高生向け、最大級のCTFです。現在は結果待ち。"},
      {title:"Milldea, LLC",date:"Since 2025.10",category:"Part-time job",link:"https://www.milldea.com/",description:"ソフトウェア開発の支援を行う会社です。"},
      {title:"基本情報技術者",date:"2025.10",category:"Certification",link:"https://www.ipa.go.jp/shiken/kubun/fe.html",description:"合格しました！"},
    ]

    const labels = {
      "Blog": "#B7E4C7",
      "CTF": "#A9C9FF",
      "Part-time job": "#FFB4A2",
      "Certification": "#FFD6A5"
    }
    
    const current = ref(0)

    onMounted(()=>{

      setInterval(()=>{

        current.value = (current.value + 1) % works.length

      },4000)

    })

    const cardWidth = 320
    const gap = 20

    const offset = computed(()=>{
      return -(current.value * (cardWidth + gap)) + (cardWidth / 2) + 50
    })

    return {works,current,labels,offset}

  }

}
</script>

<style scoped>
.works-section{
  max-width:1100px;
  margin:auto;
  padding:30px 20px;
}

h1{
  text-align: center;
  font-size: 2.5rem;
  margin-bottom: 70px;
  letter-spacing: 1px;
  color: #222;
}

h3 a {
  text-decoration: none;
  color: inherit;
}

h3 a:hover {
  text-decoration: underline;
}

.label {
  display: inline-block;
  padding: 2px 8px;
  font-size: 14px;
  border-radius: 4px;
}

.description {
  font-size: 14px;
  color: #555;
}

/* slider */
.slider{
  overflow-x: hidden;
  justify-content:center; /* ← これ追加（超重要） */
}

.slides{
  gap:20px;
  display:flex;
  transition:transform .7s ease;
}

/* card */

.card{
  width:auto;
  height: 250px;
  min-width:33.33%;
  margin:0 10px;
  flex: 0 0 320px;

  padding:28px;

  background:white;

  border-radius:12px;

  box-shadow:0 10px 25px rgba(0,0,0,0.08);

  transition:all .3s ease;

}

/* hover animation */

.card:hover{

  transform:translateY(-10px) scale(1.03);

  box-shadow:0 20px 40px rgba(0,0,0,0.15);

}

/* dots */

.dots{

  text-align:center;
  margin-top:25px;

}

.dots span{

  display:inline-block;

  width:10px;
  height:10px;

  margin:0 6px;

  border-radius:50%;

  background:#ccc;

  cursor:pointer;

  transition:.3s;

}

.dots span.active{

  background:#222;

  transform:scale(1.3);

}
</style>