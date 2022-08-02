<template>
  <div class="home">
    <header>
      <p class="header-icon">
        <span class="material-symbols-outlined">grade</span>
      </p>
    </header>

    <section class="section-title">
      <p class="p-section-title">Entrez dans l'espace.</p>
    </section>

    <section class="section">
      <div class="card-section">
        <img src="@/assets/images/planet.jpg" alt="" />
        <p class="p-section p-section-color-1">Des planètes à perte de vue.</p>
      </div>
    </section>

    <section class="section-reverse">
      <div class="card-section-reverse">
        <img src="@/assets/images/moon.jpg" alt="" />
        <p class="p-section p-section-color-1">
          Comme vous ne les avez jamais vu.
        </p>
      </div>
    </section>
  </div>
</template>

<script>
//import HelloWorld from '@/components/HelloWorld.vue'

export default {
  // name: 'HomeView',
  // components: {
  //   HelloWorld
  // }
};
</script>

<style lang="scss">
:root {
  --gradient-1: linear-gradient(-45deg, crimson, rgb(66, 47, 112));
  --gradient-2: linear-gradient(45deg, crimson, orange);

  --font-section: "Poppins", sans-serif;
}

.home {
  display: flex;
  flex-direction: column;
  & header {
    display: flex;
    justify-content: flex-end;
    & .material-symbols-outlined {
      font-size: clamp(18px, 2vw, 40px);
    }
    & .header-icon {
      padding: 1%;
      background: var(--gradient-1);
      background-clip: text;
      -webkit-background-clip: text;
      color: transparent;
      font-size: clamp(12px, 1vw, 90px);
    }
  }
  & .section-title {
    & .p-section-title {
      width: 60vw;
      margin: auto;
      background: var(--gradient-2);
      background-clip: text;
      -webkit-background-clip: text;
      font-family: var(--font-section);
      font-size: clamp(30px, 9vw, 90px);
      color: transparent;
      word-spacing: 100vw;
    }
  }
  & .section,
  .section-reverse {
    margin: 5% 0;
    & .card-section {
      display: flex;
      width: 70vw;
      margin: auto;
    }
    & .card-section-reverse {
      display: flex;
      flex-direction: row-reverse;
      width: 70vw;
      margin: auto;
    }
    & img {
      width: 40%;
      height: auto;
      border-radius: 5px;
    }
    & .p-section-color-1 {
      background: var(--gradient-1);
    }
    & .p-section {
      width: 30%;
      margin: auto;
      font-family: var(--font-section);
      font-size: clamp(15px, 4vw, 90px);
      background-clip: text;
      -webkit-background-clip: text;
      color: transparent;
    }
  }
}
</style>
