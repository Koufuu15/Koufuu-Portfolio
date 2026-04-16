<template>
  <div class="container">
    <h1>About Me</h1>

    <div class="about-grid">
      <div class="box">
        <h3>Basic Information</h3>

        <div class="info-list">
          <div class="info-item">
            <span class="label">Name</span>
            <span class="value">Koufuu</span>
          </div>

          <div class="info-item">
            <span class="label">Occupation</span>
            <span class="value">Student, Application Engineer</span>
          </div>

          <div class="info-item">
            <span class="label">Interests</span>
            <span class="value">CTF (Capture The Flag)</span>
          </div>

          <div class="info-item">
            <span class="label">Location</span>
            <span class="value">Hokkaido, Japan</span>
          </div>

          <div class="info-item">
            <span class="label">Birthday</span>
            <span class="value">29 Dec 2009</span>
          </div>

          <div class="info-item">
            <span class="label">Skills</span>
            <div class="skills">
              <span>Python</span>
              <span>JavaScript</span>
              <span>Java</span>
              <span>HTML</span>
              <span>CSS</span>
              <span>Node.js</span>
              <span>Kali Linux</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>

/* 全体 */
.container {
  max-width: 900px;
  margin: auto;
  padding: 40px 20px;
}

/* タイトル */
h1 {
  text-align: center;
  font-size: 2.5rem;
  margin-bottom: 40px;
  letter-spacing: 1px;
  color: #222;
}

/* グリッド */
.about-grid {
  display: grid;
  grid-template-columns: 1fr;
}

/* カード */
.box {
  background: white;
  border-radius: 16px;
  padding: 35px;
  box-shadow: 0 10px 25px rgba(0,0,0,0.08);
  transition: 0.3s;
}

.box:hover {
  transform: translateY(-5px);
  box-shadow: 0 20px 40px rgba(0,0,0,0.12);
}

/* 見出し */
.box h3 {
  font-size: 1.4rem;
  margin-bottom: 25px;
  border-bottom: 2px solid #eee;
  padding-bottom: 10px;
}

/* 情報リスト */
.info-list {
  display: flex;
  flex-direction: column;
  gap: 18px;
}

/* 各行 */
.info-item {
  display: grid;
  grid-template-columns: 140px 1fr;
  align-items: start;
}

/* ラベル */
.label {
  font-weight: 600;
  color: #666;
}

/* 値 */
.value {
  color: #222;
  line-height: 1.6;
}

/* スキルタグ */
.skills {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}

.skills span {
  background: #f3f4f6;
  padding: 6px 10px;
  border-radius: 8px;
  font-size: 0.85rem;
}

/* モバイル */
@media (max-width: 768px) {
  .container {
    padding: 20px 15px;
  }

  h1 {
    font-size: 2rem;
  }

  .box {
    padding: 25px 20px;
  }

  .info-item {
    grid-template-columns: 1fr;
  }

  .value {
    font-size: 0.95rem;
  }

  .skills span {
    font-size: 0.8rem;
    padding: 5px 8px;
  }
}
</style>