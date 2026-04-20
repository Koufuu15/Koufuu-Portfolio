<template>
  <div>
    <h2>Contact</h2>
    <div class="contact">
      <ul>
        <li> <!--TODO: target="_blank"の意味は？-->
          <img src="../assets/instagram.png" alt="Instagram" width="20" height="20">
          <a href="https://www.instagram.com/nade.3356/" target="_blank">Instagram</a>
        </li>
        <li>
          <img src="../assets/facebook-logo.png" alt="Facebook" width="20" height="20">
          <a href="https://www.facebook.com/profile.php?id=61577597019120" target="_blank">Facebook</a>
        </li>
        <li>
          <img src="../assets/x-logo.png" alt="X" width="20" height="20">
          <a href="https://x.com/Koufuu3356/" target="_blank">X</a>
        </li>
        <li>
          <img src="../assets/github-logo.png" alt="GitHub" width="20" height="20">
          <a href="https://github.com/Koufuu15" target="_blank">GitHub</a>
        </li>
    </ul>
  </div>
  </div>
</template>

<style scoped>
/* Contact セクション */
.contact {
  max-width: 600px;
  margin: auto;
  background: white;
  padding: 35px;
  border-radius: 12px;
  box-shadow: 0 12px 30px rgba(0,0,0,0.08);
}

/* 見出し */
h2 {
  text-align: center;
  font-size: 2rem;
  margin-bottom: 35px;
  letter-spacing: 1px;
}

/* リスト */
.contact ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

/* SNSカード */
.contact li {
  display: flex;
  align-items: center;
  gap: 12px;

  padding: 14px 18px;
  margin-bottom: 14px;

  border-radius: 10px;

  background: #f6f7fb;

  transition: all 0.25s ease;
}

/* hover */
.contact li:hover {
  transform: translateX(6px);
  box-shadow: 0 8px 18px rgba(0,0,0,0.08);
}

/* アイコン */
.contact img {
  width: 22px;
  height: 22px;
}

/* リンク */
.contact a {
  text-decoration: none;
  font-weight: 500;
  color: #333;
}

/* Instagram */
.contact li:nth-child(1):hover {
  background: linear-gradient(45deg,#feda75,#d62976,#962fbf);
}

.contact li:nth-child(1):hover a {
  color: white;
}

/* Facebook */
.contact li:nth-child(2):hover {
  background: #1877f2;
}

.contact li:nth-child(2):hover a {
  color: white;
}

/* X */
.contact li:nth-child(3):hover {
  background: #111;
}

.contact li:nth-child(3):hover a {
  color: white;
}

/* GitHub */
.contact li:nth-child(4):hover {
  background: purple;
}

.contact li:nth-child(4):hover a {
  color: white;
}
</style>