  <template>
  <div>
    <h2>Works</h2>
    <div class="works">
      <div class="card">Security Blog</div>
      <div class="card">CTF Tools</div>
      <div class="card">Web Apps</div>
    </div>
  </div>
</template>

<style scoped>
.works {
  display: grid;
  grid-template-columns: repeat(3,1fr);
  gap: 24px;
}

.card {
  background: rgba(255,255,255,0.9);
  border-radius: 16px;
  padding: 20px;
}
</style>