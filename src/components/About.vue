<template>
  <div>
    <h1>About Me</h1>
      <div class="about-grid">
        <div class="box">
          <h3>Skills</h3>
          <ul>
            <li><strong>Programming Languages:</strong><br> Python, JavaScript, Java</li>
            <li><strong>Web Development:</strong><br> HTML, CSS, Node.js</li>
            <li><strong>CTF Skills:</strong><br> Reverse Engineering, Binary Exploitation, Web Security</li>
            <li><strong>Tools:</strong><br> Wireshark, Burp Suite, Kali Linux, Ghidra, Binary ninja</li>
          </ul>
        </div>
        <div class="box">
          <h3>Basic Information</h3>
          <ul>
            <li><strong>Name:</strong><br> Koufuu</li>  <!--ゆくゆくはtabを入れてきれいにする-->
            <li><strong>Occupation:</strong><br> Student, Application Engineer</li>
            <li><strong>Interests:</strong><br> CTF (Capture The Flag) competitions</li>
            <li><strong>Location:</strong><br> Hokkaido, Japan</li>
            <li><strong>Birthday:</strong><br> 29th December, 2009</li>
          </ul>
        </div>
      </div>
  </div>
</template>

<style scoped>
/* セクション */
div {
  max-width: 1000px;
  margin: auto;
  padding: 60px 20px;
}

/* タイトル */
h1 {
  text-align: center;
  font-size: 2.5rem;
  margin-bottom: 50px;
  letter-spacing: 2px;
  color: #222;
}

/* グリッド */
.about-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 30px;
}

/* カード */
.box {
  background: white;
  border-radius: 12px;
  padding: 30px;
  box-shadow: 0 10px 25px rgba(0,0,0,0.08);
  transition: transform 0.25s ease, box-shadow 0.25s ease;
}

/* ホバー */
.box:hover {
  transform: translateY(-6px);
  box-shadow: 0 20px 40px rgba(0,0,0,0.12);
}

/* 見出し */
.box h3 {
  margin-top: 0;
  font-size: 1.4rem;
  border-bottom: 2px solid #eee;
  padding-bottom: 10px;
  margin-bottom: 20px;
}

/* リスト */
ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

li {
  margin-bottom: 18px;
  line-height: 1.6;
}

/* strong */
strong {
  color: #111;
}

/* モバイル対応 */
@media (max-width: 768px) {
  .about-grid {
    grid-template-columns: 1fr;
  }
}
</style>