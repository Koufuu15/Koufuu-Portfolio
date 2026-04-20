<template>
  <section class="hero">
    <!-- アイコン -->
    <div class="icon-wrapper">
      <img src="../assets/icon_eagle.png" alt="icon" class="icon" />
    </div>

    <!-- テキスト -->
    <h1>Hello! I am Koufuu.</h1>
    <p>An application engineer and a CTF player.</p>

    <!-- スクロール誘導 -->
    <div class="scroll-indicator">
      <span>Scroll</span>
      <div class="arrow-wrapper">
        <div class="arrow"></div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero {
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background: #f7f7f8;
  text-align: center;
  position: relative;
}

/* アイコン */
.icon-wrapper {
  margin-bottom: 24px;
}

.icon {
  width: 140px; /* ← 大きくした */
  height: 140px;
  border-radius: 50%;
  object-fit: cover;
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1); /* 少し強調 */
}

/* テキスト */
.hero h1 {
  font-size: 56px;
  margin-bottom: 12px;
}

.hero p {
  color: #666;
  font-size: 18px;
}

/* スクロール誘導 */
.scroll-indicator {
  position: absolute;
  bottom: 40px;
  display: flex;
  flex-direction: column;
  align-items: center;
  font-size: 14px;
  color: #888;
  animation: fadeIn 2s ease;
}

/* ← ここが重要 */
.arrow-wrapper {
  margin-top: 8px;
  animation: bounce 1.5s infinite;
}

.arrow {
  width: 14px; /* 少し大きく */
  height: 14px;
  border-right: 2px solid #888;
  border-bottom: 2px solid #888;
  transform: rotate(45deg); /* 回転だけ */
}

/* アニメーション */
@keyframes bounce {
  0%, 100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(8px); /* 真下に動く */
  }
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
</style>