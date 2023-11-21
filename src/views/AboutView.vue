<template>
  <div class="about">
    <h2>💻 Vue JS Todo App</h2>
    <div>
      In just one day, I dove into the world of Vue.js and crafted my very first
      project – a sleek and efficient todo app that showcases the power and
      simplicity of Vue.js. This endeavor marks the beginning of my journey into
      the realm of frontend development, and I'm excited to share the results of
      my hard work.
    </div>
    <div>
      🛠️ Tech Stack:
      <ul>
        <li>Vue.js</li>
        <li>HTML/CSS</li>
        <li>JavaScript</li>
      </ul>
    </div>

    <div>
      🎉 Conclusion:
      <div>
        Crafting this app in record time showcases my rapid grasp of Vue.js and
        sets the stage for future frontend feats. Excited for what's ahead!
      </div>
    </div>

    <div>Developed by Randolph Dy &copy; 2023</div>
  </div>
</template>

<style lang="scss">
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    max-width: 600px;
    margin: 4rem auto;
    display: flex;
    gap: 2rem;
    flex-direction: column;
    align-items: start;
  }
}

ul {
  li {
    margin-left: 3rem;
    margin-top: 0.5rem;
  }
}
</style>
