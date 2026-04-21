<template>
  <div>
    <h1>Contact</h1>
    <div class="contact">
      <ul>
        <li>
          <a href="https://www.instagram.com/nade.3356/" target="_blank">
            <img src="../assets/instagram.png" alt="Instagram">
            <span>Instagram</span>
          </a>
        </li>

        <li>
          <a href="https://www.facebook.com/profile.php?id=61577597019120" target="_blank">
            <img src="../assets/facebook-logo.png" alt="Facebook">
            <span>Facebook</span>
          </a>
        </li>

        <li>
          <a href="https://x.com/Koufuu3356/" target="_blank">
            <img src="../assets/x-logo.png" alt="X">
            <span>X</span>
          </a>
        </li>

        <li>
          <a href="https://github.com/Koufuu15" target="_blank">
            <img src="../assets/github-logo.png" alt="GitHub">
            <span>GitHub</span>
          </a>
        </li>
      </ul>
    </div>
  </div>
</template>

<style scoped>

/* 全体 */
.contact {
  width: 100%;
  padding: 40px 5%;
  transform: translateY(-40px);
  box-sizing: border-box;
}

/* 見出し */
h1 {
  text-align: center;
  font-size: 2.5rem;
  margin-bottom: 30px;
  letter-spacing: 1px;
  color: #222;
}

/* グリッド */
.contact ul {
  display: grid;
  grid-template-columns: 1fr; 
  
  gap: 20px;

  list-style: none;
  padding: 0;
  margin: 0;
}

/* タブレット以上 */
@media (min-width: 768px) {
  .contact ul {
    grid-template-columns: repeat(2, 1fr);
    gap: 30px;
  }
}

/* PC */ 
@media (min-width: 1024px) {
  .contact ul {
    grid-template-columns: repeat(4, 1fr);
  }
}


/* カード */
.contact li {
  border-radius: 14px;
  background: white;
  box-shadow: 0 10px 25px rgba(0,0,0,0.08);
  transition: all 0.3s ease;
  aspect-ratio: 7 / 4; /* 横長の比率を維持 */
  width: 100%; /* カードが親の幅いっぱいに広がる */
}

/* リンク */
.contact a {
  flex-direction: column;

  display: flex;
  align-items: center;
  justify-content: center;
  gap: 14px;

  padding: 24px;
  text-decoration: none;
  color: #333;
  font-weight: 500;
}

/* hover */
.contact li:hover {
  transform: translateY(-6px) scale(1.03);
  box-shadow: 0 14px 30px rgba(0,0,0,0.12);
}

/* アイコン */
.contact img {
  width: 28px;
  height: 28px;
}

/* SNS hover色 */
.contact li:nth-child(1):hover {
  background: linear-gradient(45deg,#feda75,#d62976,#962fbf);
}
.contact li:nth-child(1):hover a { color: white; }

.contact li:nth-child(2):hover {
  background: #1877f2;
}
.contact li:nth-child(2):hover a { color: white; }

.contact li:nth-child(3):hover {
  background: #111;
}
.contact li:nth-child(3):hover a { color: white; }

.contact li:nth-child(4):hover {
  background: purple;
}
.contact li:nth-child(4):hover a { color: white; }

</style>

