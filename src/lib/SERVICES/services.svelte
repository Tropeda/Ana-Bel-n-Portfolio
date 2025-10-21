<script>
  const services = [
    {
      title: "DESIGN",
      desc: "I create modern, clean, and user-friendly interfaces focused on the user experience.",
      icon: "icono-design.png", // ruta a tu icono
      active: true
    },
    {
      title: "WEB DEVELOPMENT",
      desc: "I build web pages using HTML, CSS, JavaScript, and Svelte, with responsive and dynamic designs.",
      icon: "icono-web.png",
      active: false
    },
    {
      title: "OPTIMISATION",
      desc: "I ensure that the website loads quickly, is lightweight, and works well on all devices.",
      icon: "icono-engranaje.png", // emoji opcional
      active: false
    },
    {
      title: "MAINTENANCE",
      desc: "I update and improve existing websites so that they are always up to date and in good condition.",
      icon: "icono-llaves.png",
      active: false
    }
  ];
</script>
<section id="services"> </section>
<section class="services">
  <div class="header">
    <div>
      <h2><span class="white">My</span> <span class="green">Services</span></h2>
    </div>
  </div>

  <div class="cards">
    {#each services as service}
      <div class="card {service.active ? 'active' : ''}">
        <div class="shine"></div>
        <div class="icon">
          {#if service.icon.endsWith(".png") || service.icon.endsWith(".svg")}
            <img src="{service.icon}" alt="{service.title} icon" />
          {:else}
            {service.icon} <!-- emoji o texto -->
          {/if}
        </div>
        <h3>{service.title}</h3>
        <p>{service.desc}</p>
      </div>
    {/each}
  </div>
</section>

<style>
@import url('https://fonts.googleapis.com/css2?family=Lato:wght@400;700&display=swap');

:root {
  --color1: #060408;
  --color2: #312935;
  --color3: #696377;
  --color4: #a7a4b6;
  --color5: #ead9e7;
  --accent-red: #931449;
}

.services {
  background: var(--color1);
  color: white;
  padding: 4rem 2rem 6rem;
  font-family: 'Lato', sans-serif;
}

.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 3rem;
}

h2 {
  font-size: 2.5rem;
  font-weight: bold;
}

.white {
  color: var(--accent-red);
}

.green {
  color: white;
}

.cards {
  display: flex;
  gap: 2rem;
  justify-content: center;
  flex-wrap: wrap;
}

.card {
  background: var(--accent-red);
  padding: 2rem;
  border-radius: 2rem;
  text-align: center;
  flex: 1 1 250px;
  transition: 0.3s ease;
  position: relative;
  overflow: hidden;
}

.card.active {
  background: var(--accent-red);
  color: white;
}

.shine {
  position: absolute;
  top: -50%;
  left: -50%;
  width: 40%;
  height: 200%;
  background: linear-gradient(
    90deg,
    rgba(255, 255, 255, 0) 0%,
    rgba(255, 255, 255, 0.3) 50%,
    rgba(255, 255, 255, 0) 100%
  );
  transform: rotate(25deg);
  transition: left 0.6s ease;
  pointer-events: none;
}

.card:hover .shine {
  left: 150%;
}

.icon {
  font-size: 2.5rem;
  margin-bottom: 1rem;
  position: relative;
  z-index: 1;
}

.icon img {
  width: 50px;
  height: 50px;
  object-fit: contain;
  margin-bottom: 1rem;
}

h3 {
  font-size: 1.2rem;
  margin-bottom: 0.5rem;
  position: relative;
  z-index: 1;
}

p {
  font-size: 1.1rem;
  margin-bottom: 1rem;
  margin-top: 20px;
  position: relative;
  z-index: 1;
}


</style>