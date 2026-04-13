<template>
  <div class="works-section">

    <h2>Works</h2>

    <div class="slider">

      <div
        class="slides"
        :style="{ transform:`translateX(-${current * (100/3)}%)` }"
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
        </div>

      </div>

    </div>

    <!-- dots -->
    <div class="dots">
      <span
        v-for="(w,i) in works"
        :key="i"
        :class="{active: i===(current + 1) % works.length}"
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
      {title:"Zenn",date:"Since 2025",category:"Blog",link:"https://zenn.dev/koufu"},
      {title:"Qiita",date:"Since 2025",category:"Blog",link:"https://qiita.com/nade_3356"},
      {title:"picoCTF",date:"2026.3",category:"CTF",link:"https://github.com/0x00h/web-apps"},
      {title:"Milldea, LLC",date:"Since 2025.10",category:"Part-time job",link:"https://www.milldea.com/"}
    ]

    const labels = {
      "Blog": "#B7E4C7",
      "CTF": "#A9C9FF",
      "Part-time job": "#FFB4A2"
    }
    
    const current = ref(0)

    onMounted(()=>{

      setInterval(()=>{

        current.value = (current.value + 1) % works.length

      },4000)

    })

    return {works,current,labels}

  }

}
</script>

<style scoped>
.works-section{
  max-width:1100px;
  margin:auto;
  padding:30px 20px;
}

h2{
  margin-bottom:40px;
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

/* slider */

.slider{
  overflow-x:hidden;
}

.slides{
  display:flex;
  transition:transform .7s ease;
}

/* card */

.card{
  height: 200px;
  min-width:33.33%;
  margin:0 10px;

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