<template>
  <div class="works-section">

    <h1>Works</h1>

    <div class="carousel">

      <!-- 左ボタン -->
      <button class="nav prev" @click="prev" v-show="current!==0">‹</button>

      <div class="track">

        <div
          v-for="(work,i) in works"
          :key="i"
          class="card"
          :class="{ active: i === current }"
        >
          <h3>
            <a :href="work.link" target="_blank" rel="noopener noreferrer">
              {{work.title}}
            </a>
          </h3>
          <p>{{work.date}}</p>
          <span class="label" :style="{ backgroundColor: labels[work.category] }">
            {{work.category}}
          </span>
          <p class="description">
            {{work.description}}
          </p>
        </div>

      </div>

      <!-- 右ボタン -->
      <button class="nav next" @click="next" v-show="current!==works.length-1">›</button>

    </div>

  </div>
</template>

<script>
import { ref } from "vue"

export default {
  setup(){

    const works = [
      {title:"Zenn",date:"Since 2025",category:"Blog",link:"https://zenn.dev/koufu",description:"技術ブログ。主にCTFやセキュリティに関する内容を投稿しています。"},
      {title:"Qiita",date:"Since 2025",category:"Blog",link:"https://qiita.com/nade_3356",description:"技術ブログ。学校のオーガニゼーションと結びついています。"},
      {title:"CognitiveHack Japan",date:"2026.3",category:"CTF",link:"https://cognitivehack-jp.cognitivectf.com/",description:"中高生向け、最大級のCTFです。現在は結果待ち。"},
      {title:"インターンシップ",date:"Since 2025.10",category:"Part-time job",description:"Web開発を担当しています。"},
      {title:"基本情報技術者",date:"2025.10",category:"Certification",link:"https://www.ipa.go.jp/shiken/kubun/fe.html",description:"合格しました！"},
      {title:"IELTS 6.5",date:"2025.6",category:"Certification",link:"https://ieltsjp.com/japan",description:"現在も勉強中です。"},
      {title:"高等学校卒業程度認定試験",date:"2025.8",category:"Certification",link:"https://www.mext.go.jp/a_menu/koutou/shiken/",description:"何のために？ そんなの知りません。"},
      {title:"書道六段",date:"2025.10 ~ now",category:"Certification",link:"http://syokyuin.net/",description:"地味に歴１０年"}
    ]

    const labels = {
      "Blog": "#B7E4C7",
      "CTF": "#A9C9FF",
      "Part-time job": "#FFB4A2",
      "Certification": "#FFD6A5"
    }

    const current = ref(0)

    const next = ()=>{
      current.value = (current.value + 1) % works.length
    }

    const prev = ()=>{
      current.value = (current.value - 1 + works.length) % works.length
    }

    return {works,labels,current,next,prev}
  }
}
</script>

<style scoped>

/* ===== layout ===== */
.works-section{
  width:100%;
  padding:60px 5vw;
  text-align:center;
  transform: translateY(-40px);
}

h1{
  text-align:center;
  font-size:2.5rem;
  margin-bottom:60px;
  color:#222;
}

h3 a {
  text-decoration:none;
  color:inherit;
}

h3 a:hover {
  text-decoration:underline;
}

.carousel{
  position:relative;
  display:flex;
  align-items:center;
  justify-content:center;
}

/* ===== track ===== */
.track{
  position:relative;
  width:100%;
  height:260px;
}

/* ===== card ===== */
.card{
  position:absolute;
  top:50%;
  left:50%;

  width:70%;
  max-width:600px;

  transform:translate(-50%,-50%) scale(0.8);
  opacity:0;

  padding:30px;
  border-radius:16px;

  background:white;
  box-shadow:0 10px 30px rgba(0,0,0,0.1);

  transition:all .5s ease;
}

/* 中央 */
.card.active{
  transform:translate(-50%,-50%) scale(1);
  opacity:1;
  z-index:3;
}

/* 左右のカード */
.card:not(.active){
  opacity:0.4;
  z-index:1;
}

/* ===== nav ===== */
.nav{
  z-index:10;
  position:absolute;
  top:50%;
  transform:translateY(-50%);

  width:45px;
  height:45px;

  border:none;
  border-radius:50%;

  background:white;
  box-shadow:0 5px 15px rgba(0,0,0,0.15);

  font-size:24px;
  cursor:pointer;
}

.prev{ left:10px; }
.next{ right:10px; }

/* ===== label ===== */
.label{
  display:inline-block;
  padding:3px 10px;
  border-radius:6px;
  font-size:13px;
  margin-top:10px;
}

.description{
  font-size:14px;
  color:#555;
  margin-top:10px;
}
</style>