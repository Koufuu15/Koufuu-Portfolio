<template>
  <div class="works-section">

    <h1>Works</h1>

    <div class="slider">

      <!-- ← -->
      <button class="nav prev" @click="prev">‹</button>

      <div
        class="slides"
        :style="{ transform:`translateX(calc(-${current * (100/3)}% + 33.33%))` }"
      >

        <div
          class="card"
          v-for="(work,i) in works"
          :key="i"
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

      <!-- → -->
      <button class="nav next" @click="next">›</button>

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
import {ref,onMounted} from "vue"

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

    const next = ()=>{
      current.value = (current.value + 1) % works.length
    }

    const prev = ()=>{
      current.value = (current.value - 1 + works.length) % works.length
    }

    onMounted(()=>{
      setInterval(()=> next(),4000)
    })

    return {works,current,labels,next,prev}
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
  text-align:center;
  font-size:2.5rem;
  margin-bottom:70px;
  color:#222;
}

h3 a {
  text-decoration:none;
  color:inherit;
}

h3 a:hover {
  text-decoration:underline;
}

.label{
  display:inline-block;
  padding:2px 8px;
  font-size:14px;
  border-radius:4px;
}

.description{
  font-size:14px;
  color:#555;
  margin-top:10px;
}

/* ===== slider ===== */
.slider{
  overflow:hidden; /* 横は切る（チラ見せ） */
  position:relative;
}

.slides{
  display:flex;
  transition:transform .7s ease;
}

/* ===== card ===== */
.card{
  min-width:33.33%;
  margin:0 10px;

  height:250px;
  padding:28px;

  background:white;
  border-radius:12px;

  box-shadow:0 10px 25px rgba(0,0,0,0.08);
  transition:all .3s ease;
}

.card:hover{
  transform:translateY(-10px) scale(1.03);
  box-shadow:0 20px 40px rgba(0,0,0,0.15);
}

/* ===== nav ===== */
.nav{
  position:absolute;
  top:50%;
  transform:translateY(-50%);
  z-index:10;

  width:40px;
  height:40px;

  border:none;
  border-radius:50%;
  background:white;
  box-shadow:0 5px 15px rgba(0,0,0,0.15);

  cursor:pointer;
  font-size:22px;
}

.prev{ left:10px; }
.next{ right:10px; }

/* ===== dots ===== */
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
}

.dots span.active{
  background:#222;
  transform:scale(1.3);
}

</style>