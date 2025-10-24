<script>
  let activeIndex = 0;
  let isHovering = false;
  let mouseX = 0;
  let mouseY = 0;
  
  const projects = [
    {
      id: 1,
      title: "Hedelweb",
      description: "Website to showcase the work, projects and services of a start-up company of web designers and developers.",
      image: "lasproject.png",
      color: "#931449"
    },
    {
      id: 2,
      title: "Construction company website",
      description: "Complete overhaul of an outdated website for a construction company",
      image: "genaysa.png",
      color: "#931449"
    },
    {
      id: 3,
      title: "Task Manager",
      description: "Task manager with AI-driven suggestions and workflow automation.",
      image: "taskmanager.png",
      color: "#931449"
    },
    {
      id: 4,
      title: "Nightclub website",
      description: "Website created for a nightclub using various creative effects and with the option to listen to music on the website itself.",
      image: "clubweb.png",
      color: "#931449"
    }
  ];

  /**
   * @param {{ clientX: number; clientY: number; }} event
   */
  function handleMouseMove(event) {
    mouseX = event.clientX;
    mouseY = event.clientY;
  }

  // Auto-rotación de proyectos
  setInterval(() => {
    if (!isHovering) {
      activeIndex = (activeIndex + 1) % projects.length;
    }
  }, 5000);
</script>

<svelte:window on:mousemove={handleMouseMove} />

<section class="portfolio-section">
  <!-- Fondo animado con partículas -->
  <div class="particles">
    {#each Array(20) as _, i}
      <div 
        class="particle" 
        style="
          left: {Math.random() * 100}%;
          top: {Math.random() * 100}%;
          animation-delay: {Math.random() * 5}s;
          animation-duration: {3 + Math.random() * 4}s;
        "
      ></div>
    {/each}
  </div>

  <!-- Cursor personalizado -->
  <div 
    class="custom-cursor" 
    style="transform: translate({mouseX}px, {mouseY}px)"
  ></div>

  <div class="container">
    <!-- Header -->
    <div class="header">
      <span class="label">— My Work</span>
      <h2 class="main-title">
        Projects that Bring Ideas <span class="gradient-text">to Life</span> 
      </h2>
    </div>

    <!-- Grid de proyectos -->
    <div class="projects-grid">
      {#each projects as project, index}
        <div 
          class="project-card {activeIndex === index ? 'active' : ''}"
          on:mouseenter={() => { activeIndex = index; isHovering = true; }}
          on:mouseleave={() => { isHovering = false; }}
          role="article"
          style="--accent-color: {project.color}"
        >
          <!-- Imagen con overlay -->
          <div class="image-container">
            <img src={project.image} alt={project.title} />
            <div class="overlay">
              <div class="overlay-content">
                <span class="category">{project.category}</span>
                <a href={project.link} target="_blank" rel="noopener" class="view-btn">
                  <span>Ver Proyecto</span>
                  <svg width="20" height="20" viewBox="0 0 24 24" fill="none">
                    <path d="M7 17L17 7M17 7H7M17 7V17" stroke="currentColor" stroke-width="2" stroke-linecap="round"/>
                  </svg>
                </a>
              </div>
            </div>
          </div>

          <!-- Información del proyecto -->
          <div class="card-content">
            <h3 class="project-title">{project.title}</h3>
            <p class="project-description">{project.description}</p>
            
            <!-- Tecnologías -->
            <div class="tech-stack">
              {#each project.tech as tech}
                <span class="tech-tag">{tech}</span>
              {/each}
            </div>
          </div>

          <!-- Indicador de proyecto activo -->
          <div class="active-indicator"></div>
        </div>
      {/each}
    </div>

    <!-- Navegación con dots -->
    <div class="navigation">
      {#each projects as _, index}
        <button
          class="dot {activeIndex === index ? 'active' : ''}"
          on:click={() => activeIndex = index}
          aria-label="Proyecto {index + 1}"
        ></button>
      {/each}
    </div>
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

  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  .portfolio-section {
    min-height: 100vh;
    background:white;
    color: var(--color1);
    padding: 6rem 2rem;
    position: relative;
    overflow: hidden;
    font-family: 'Inter', sans-serif;
  }

  /* Partículas de fondo */
  .particles {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    pointer-events: none;
    z-index: 1;
  }

  .particle {
    position: absolute;
    width: 4px;
    height: 4px;
    background:var(--accent-red);
    border-radius: 50%;
    animation: float infinite ease-in-out;
  }

  @keyframes float {
    0%, 100% { transform: translateY(0) scale(1); opacity: 0.3; }
    50% { transform: translateY(-30px) scale(1.2); opacity: 0.8; }
  }

  /* Cursor personalizado */
  .custom-cursor {
    position: fixed;
    width: 40px;
    height: 40px;
    border: 2px var(--accent-red);
    border-radius: 50%;
    pointer-events: none;
    z-index: 9999;
    transition: transform 0.15s ease-out;
    mix-blend-mode: difference;
  }

  .container {
    max-width: 1400px;
    margin: 0 auto;
    position: relative;
    z-index: 2;
  }

  /* Header */
  .header {
    text-align: center;
    margin-bottom: 5rem;
    animation: fadeInDown 1s ease-out;
  }

  .label {
    display: inline-block;
    font-size: 0.9rem;
    font-weight: 600;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: var(--color3);
    margin-bottom: 1rem;
  }

  .main-title {
    font-size: clamp(2.5rem, 5vw, 4rem);
    font-weight: 800;
    line-height: 1.2;
    margin-bottom: 1.5rem;
    font-family: 'Lato', sans-serif;
  }

  .gradient-text {
    background: var(--accent-red);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .subtitle {
    font-size: 1.1rem;
    color:var(--color4);
    max-width: 600px;
    margin: 0 auto;
  }

  /* Grid de proyectos */
  .projects-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
    margin-bottom: 3rem;
  }

  .project-card {
    background: var(--accent-red);
    border-radius: 20px;
    overflow: hidden;
    position: relative;
    transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
    border: 1px solid rgba(255, 255, 255, 0.1);
    backdrop-filter: blur(10px);
  }

  .project-card:hover {
    transform: translateY(-10px);
    box-shadow: 0 20px 60px rgba(0, 0, 0, 0.4);
    border-color:var(--color5);
  }

  .project-card.active {
    border-color: var(--accent-color);
    box-shadow: 0 0 40px rgba(255, 255, 255, 0.1);
  }

  /* Imagen */
  .image-container {
    position: relative;
    overflow: hidden;
    height: 280px;
  }

  .image-container img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform 0.6s ease;
  }

  .project-card:hover .image-container img {
    transform: scale(1.1);
  }

  .overlay {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: linear-gradient(135deg, rgba(0, 0, 0, 0.7) 0%, rgba(147, 20, 73) 90%);
    display: flex;
    align-items: center;
    justify-content: center;
    opacity: 0;
    transition: opacity 0.5s ease;
  }

  .project-card:hover .overlay {
    opacity: 1;
  }

  .overlay-content {
    text-align: center;
    transform: translateY(20px);
    transition: transform 0.4s ease;
  }

  .project-card:hover .overlay-content {
    transform: translateY(0);
  }

  .view-btn {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    padding: 0.8rem 1.5rem;
    background: white;
    color: #000;
    text-decoration: none;
    border-radius: 30px;
    font-weight: 600;
    transition: all 0.3s ease;
  }

  .view-btn:hover {
    transform: scale(1.05);
    box-shadow: 0 10px 30px rgba(255, 255, 255, 0.3);
  }

  /* Contenido de la card */
  .card-content {
    padding: 2rem;
  }

  .project-title {
    font-size: 1.5rem;
    font-weight: 700;
    margin-bottom: 1rem;
    color: #fff;
  }

  .project-description {
    font-size: 0.95rem;
    color: var(--white);
    line-height: 1.6;
    margin-bottom: 1.5rem;
  }

  /* Stack tecnológico */
  .tech-stack {
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
  }

  .tech-tag {
    padding: 0.4rem 0.8rem;
    background: rgba(255, 255, 255, 0.1);
    border-radius: 15px;
    font-size: 0.75rem;
    font-weight: 500;
    color: var(--accent-color);
    border: 1px solid rgba(255, 255, 255, 0.2);
  }

  /* Indicador activo */
  .active-indicator {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 4px;
    background: var(--accent-color);
    transform: scaleX(0);
    transform-origin: left;
    transition: transform 0.4s ease;
  }

  .project-card.active .active-indicator {
    transform: scaleX(1);
  }

  /* Navegación */
  .navigation {
    display: flex;
    justify-content: center;
    gap: 1rem;
  }

  .dot {
    width: 12px;
    height: 12px;
    border-radius: 50%;
    background: rgba(255, 255, 255, 0.3);
    border: none;
    cursor: pointer;
    transition: all 0.3s ease;
  }

  .dot:hover {
    background: rgba(255, 255, 255, 0.6);
    transform: scale(1.2);
  }

  .dot.active {
    background: var(--accent-red);
    width: 30px;
    border-radius: 10px;
  }

  /* Animaciones */
  @keyframes fadeInDown {
    from {
      opacity: 0;
      transform: translateY(-30px);
    }
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }

  /* Responsive */
  @media (max-width: 768px) {
    .portfolio-section {
      padding: 4rem 1rem;
    }

    .header {
      margin-bottom: 3rem;
    }

    .projects-grid {
      grid-template-columns: 1fr;
      gap: 1.5rem;
    }

    .custom-cursor {
      display: none;
    }
  }

  @media (min-width: 769px) and (max-width: 1024px) {
    .projects-grid {
      grid-template-columns: repeat(2, 1fr);
    }
  }
</style>