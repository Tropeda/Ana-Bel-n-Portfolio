<script>
  let stats = [
    { number: "600+", label: "Practical Hours" },
    { number: "200+", label: "Sleepless Hours" }
  ];

  const cvPath = "/CV Ana-Belén.pdf";

  function downloadCV() {
    // Crear un enlace temporal para la descarga
    const link = document.createElement('a');
    link.href = cvPath;
    link.download = 'Ana_Belen_CV.pdf'; // Nombre con el que se descargará
    document.body.appendChild(link);
    link.click();
    document.body.removeChild(link);
  }
</script>

<section class="about-section">
  <section id="about" class="about-section">
</section>
  <!-- Ola superior -->
  <div class="wave wave-top">
    <svg viewBox="0 0 1200 120" preserveAspectRatio="none">
      <path d="M0,0 C150,100 350,0 600,50 C850,100 1050,0 1200,50 L1200,0 L0,0 Z" fill="#000000"></path>
    </svg>
  </div>

  <div class="container">
    <div class="experience-card">
      <div class="vertical-text">ANA BELÉN</div>
      <div class="years-number">VI</div>
      <div class="years-text">Months of Experience</div>
    </div>

    <div class="content">
      <div class="header">
        <span class="dash">—</span>
        <span class="subtitle">About Me</span>
      </div>
      
      <h1 class="title">
        Who is <span class="name">Ana</span>?
      </h1>
      
      <p class="description">
        Hello! I'm Ana, a 25-year-old web developer from Malaga. <br>
        My story with coding is a bit unexpected. A few years ago, programming seemed like 'alien technology' to me, something complex and unattainable. But one summer I decided to take the plunge, and it was love at first line of code! Since then, I haven't stopped researching, practising and developing my skills.
        I am passionate about turning ideas into functional and engaging digital experiences. <br/><br/>

        Beyond my passion for development, you'll find me exploring worlds in video games, immersed in a good book, or planning my next travel adventure.
        If you're looking for someone with curiosity, energy, and a desire to create amazing things, let's talk!
      </p>

      <div class="stats">
        {#each stats as stat}
          <div class="stat-item">
            <div class="stat-number">{stat.number}</div>
            <div class="stat-label">{stat.label}</div>
          </div>
        {/each}
      </div>

      <div class="actions">
        <button class="download-btn" on:click={downloadCV}>
          <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4M7 10l5 5 5-5M12 15V3"/>
          </svg>
          Download CV
        </button>
      </div>
    </div>
  </div>
 
  <!-- Ola inferior -->
  <div class="wave wave-bottom">
    <svg viewBox="0 0 1200 120" preserveAspectRatio="none">
      <path d="M0,0 C150,100 350,0 600,50 C850,100 1050,0 1200,50 L1200,120 L0,120 Z" fill="white"></path>
    </svg>
  </div> 
</section>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@400;500;600;700&family=Dancing+Script:wght@700&display=swap');

  :root {
    --color1: #060408;
    --color2: #312935;
    --color3: #696377;
    --color4: #a7a4b6;
    --color5: #ead9e7;
    --accent-red: #931449;
    --white: #ffffff;
  }

  .about-section {
    background: var(--white);
    padding: 6rem 2rem;
    font-family: 'Space Grotesk', sans-serif;
    position: relative;
    min-height: 100vh;
    display: flex;
    align-items: center;
  }

  .wave {
    position: absolute;
    left: 0;
    width: 100%;
    overflow: hidden;
    line-height: 0;
    z-index: 1;
  }

  .wave-top {
    top: -1px;
  }

  .wave-bottom {
    bottom: -1px;
  }

  .wave svg {
    position: relative;
    display: block;
    width: calc(100% + 1.3px);
    height: 95px;
  }

  .container {
    max-width: 1200px;
    margin: 0 auto;
    display: flex;
    gap: 3rem;
    align-items: center;
    flex-wrap: wrap;
    position: relative;
    z-index: 2;
    width: 100%;
  }

  .experience-card {
    background: #931449;
    border-radius: 2rem;
    padding: 3rem 2.5rem;
    color: white;
    position: relative;
    min-width: 350px;
    flex: 0 0 350px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    margin-top: -70px;
    box-shadow: 0 20px 60px rgba(147, 20, 73, 0.2);
  }

  .vertical-text {
    position: absolute;
    left: -148px;
    top: 50%;
    transform: translateY(-60%) rotate(-90deg);
    font-weight: 800;
    font-size: 3rem;
    letter-spacing: 0.15em;
    white-space: nowrap;
    color: white;
  }

  .years-number {
    font-size: 15rem;
    font-weight: 600;
    line-height: 1;
    letter-spacing: -0.02em;
    margin-bottom: 0.4rem;
  }

  .years-text {
    font-size: 1.1rem;
    font-weight: 800;
    text-align: center;
    margin-top: 25px;
  }

  .content {
    flex: 1;
    min-width: 300px;
  }

  .header {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    margin-bottom: 1rem;
  }

  .dash {
    color: #2d3748;
    font-weight: 600;
    font-size: 1.5rem;
  }

  .subtitle {
    color: #4a5568;
    font-size: 0.95rem;
    font-weight: 500;
    letter-spacing: 0.05em;
  }

  .title {
    font-size: 3rem;
    font-weight: 700;
    color: #1a202c;
    margin-bottom: 1.5rem;
    line-height: 1.2;
  }

  .name {
    color: var(--accent-red);
  }

  .description {
    color: var(--color1);
    font-size: 1.2rem;
    line-height: 1.7;
    margin-bottom: 2.5rem;
    max-width: 700px;
  }

  .stats {
    display: flex;
    gap: 4rem;
    margin-bottom: 2.5rem;
  }

  .stat-item {
    display: flex;
    flex-direction: column;
  }

  .stat-number {
    font-size: 2.5rem;
    font-weight: 700;
    color: var(--color1);
    margin-bottom: 0.3rem;
  }

  .stat-label {
    color: #4a5568;
    font-size: 1rem;
    font-weight: 500;
  }

  .actions {
    display: flex;
    align-items: center;
    gap: 2rem;
    flex-wrap: wrap;
  }

  .download-btn {
    background: #931449;
    color: white;
    border: none;
    border-radius: 50px;
    padding: 0.9rem 2rem;
    font-size: 1rem;
    font-weight: 600;
    cursor: pointer;
    display: flex;
    align-items: center;
    gap: 0.5rem;
    transition: transform 0.3s ease, box-shadow 0.3s ease;
    font-family: 'Space Grotesk', sans-serif;
  }

  .download-btn:hover {
    transform: translateY(-2px);
    box-shadow: 0 10px 25px rgba(147, 20, 73, 0.3);
  }

  .download-btn svg {
    width: 20px;
    height: 20px;
  }

  /* PANTALLAS GRANDES (Monitores de escritorio grandes) */
  @media (min-width: 1400px) {
    .container {
      max-width: 1400px;
      gap: 5rem;
    }

    .experience-card {
      min-width: 400px;
      flex: 0 0 400px;
      padding: 4rem 3rem;
    }

    .years-number {
      font-size: 17rem;
    }

    .vertical-text {
      font-size: 3.5rem;
      left: -168px;
    }

    .title {
      font-size: 3.5rem;
    }

    .description {
      font-size: 1.3rem;
      max-width: 800px;
    }

    .stat-number {
      font-size: 3rem;
    }

    .stat-label {
      font-size: 1.1rem;
    }
  }

  /* TABLETS Y PANTALLAS MEDIANAS */
  @media (max-width: 1024px) and (min-width: 769px) {
    .container {
      gap: 2.5rem;
    }

    .experience-card {
      min-width: 300px;
      flex: 0 0 300px;
      padding: 2.5rem 2rem;
    }

    .vertical-text {
      font-size: 2.5rem;
      left: -120px;
    }

    .years-number {
      font-size: 12rem;
    }

    .title {
      font-size: 2.5rem;
    }

    .description {
      font-size: 1.1rem;
    }
  }

  /* TABLETS PEQUEÑAS */
  @media (max-width: 768px) {
    .about-section {
      padding: 4rem 1.5rem;
      min-height: auto;
    }

    .wave svg {
      height: 60px;
    }

    .container {
      flex-direction: column;
      gap: 2rem;
    }

    .experience-card {
      min-width: 100%;
      max-width: 400px;
      flex: 1;
      margin-top: 0;
      padding: 2.5rem 2rem;
    }

    .vertical-text {
      display: none;
    }

    .years-number {
      font-size: 10rem;
    }

    .years-text {
      font-size: 1rem;
      margin-top: 20px;
    }

    .content {
      width: 100%;
    }

    .title {
      font-size: 2.2rem;
    }

    .description {
      font-size: 1.1rem;
      margin-bottom: 2rem;
    }

    .stats {
      gap: 2.5rem;
      justify-content: center;
    }

    .stat-number {
      font-size: 2.2rem;
    }

    .stat-label {
      font-size: 0.95rem;
    }

    .actions {
      justify-content: center;
    }
  }

  /* MÓVILES */
  @media (max-width: 480px) {
    .about-section {
      padding: 3rem 1rem;
    }

    .wave svg {
      height: 40px;
    }

    .experience-card {
      padding: 2rem 1.5rem;
      border-radius: 1.5rem;
      max-width: 100%;
    }

    .years-number {
      font-size: 8rem;
    }

    .years-text {
      font-size: 0.9rem;
      margin-top: 15px;
    }

    .header {
      margin-bottom: 0.8rem;
    }

    .dash {
      font-size: 1.2rem;
    }

    .subtitle {
      font-size: 0.85rem;
    }

    .title {
      font-size: 1.8rem;
      margin-bottom: 1.2rem;
    }

    .description {
      font-size: 1rem;
      line-height: 1.6;
      margin-bottom: 1.8rem;
    }

    .description br {
      display: none;
    }

    .stats {
      flex-direction: column;
      gap: 1.5rem;
      align-items: center;
      text-align: center;
      margin-bottom: 2rem;
    }

    .stat-number {
      font-size: 2rem;
    }

    .stat-label {
      font-size: 0.9rem;
    }

    .download-btn {
      width: 100%;
      justify-content: center;
      padding: 1rem 1.5rem;
    }
  }

  /* MÓVILES MUY PEQUEÑOS */
  @media (max-width: 360px) {
    .title {
      font-size: 1.6rem;
    }

    .years-number {
      font-size: 7rem;
    }

    .description {
      font-size: 0.95rem;
    }

    .stat-number {
      font-size: 1.8rem;
    }
  }
</style>