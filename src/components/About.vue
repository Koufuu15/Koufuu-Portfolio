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
.about-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 32px;
}

.box {
  background: rgba(255,255,255,0.8);
  border-radius: 16px;
  padding: 24px;
}
</style>